# SA-tensorflow
Tensorflow implementation of soft-attention mechanism for video caption generation. 
<center>
<img src="./README_files/system.png">
An example of soft-attention mechanism. The attention weight alpha indicates the temporal attention in one video based on each word.  
</center>

[[Yao et al. 2015 Describing Videos by Exploiting Temporal Structure]](http://arxiv.org/abs/1502.08029)
The original code implemented in Torch can be found [here](https://github.com/yaoli/arctic-capgen-vid).
# Prerequisites
* Python 2.7
* [Tensorflow](https://www.tensorflow.org/) >= 0.7.1
* NumPy
* pandas
* keras
* java 1.8.0

# Data
We pack the data into the format of HDF5, where each file has the following keys:
```
[u'data', u'fname', u'label', u'title']
```

```a['data']``` stores the visual features. ```shape (n_step_lstm, batch_size, hidden_dim) ```

```a['fname']``` stores the filenames(no extension) of videos. ```shape (batch_size)```

```a['title']``` stores the description. If there are multiple sentences correspond to one video, the other metadata such as visual features, filenames and labels have to duplicate for one-to-one mapping. ```shape (batch_size)```

```a['label']``` indicates where the video ends. For instance, ```[-1., -1., -1., -1.,  0., -1., -1.]``` means that the video ends at index 4.

```shape (n_step_lstm, batch_size)```

# Usage

## training
```
$ python Att.py --task train
```
## testing
You test the model after a certain number of training epochs.

```
$ python Att.py --task test --net models/model-20
```
## Auther
[Tseng-Hung Chen](https://github.com/paul0819)

[Kuo-Hao Zeng](https://github.com/jacky55062003)

## Acknowledgments

We modified the code from this repository [jazzsaxmafia/video\_to\_sequence](https://github.com/jazzsaxmafia/video_to_sequence) to the temporal-attention model.

## Reference

[1] L. Yao, A. Torabi, K. Cho, N. Ballas, C. Pal, H. Larochelle, and A. Courville. 
Describing videos by exploiting temporal structure. arXiv:1502.08029v4, 2015.

[2] chen:acl11,
  title = "Collecting Highly Parallel Data for Paraphrase Evaluation",
  author = "David L. Chen and William B. Dolan",
  booktitle = "Proceedings of the 49th Annual Meeting of the Association for Computational Linguistics (ACL-2011)",
  address = "Portland, OR",
  month = "June",
  year = 2011

[3] [Microsoft COCO Caption Evaluation](https://github.com/tylin/coco-caption)
