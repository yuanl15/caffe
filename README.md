## Introduction
This is my repository to study Caffe, which is a great deep learning framework.There are some annotations in this work to clarify the code of framework.I think that the programer can improve a lot from the code of Caffe.   
caffe是深度学习领域优秀的框架，深入其源码有助于更好地应用caffe，更能够通过阅读优秀的代码实践，来提升自己的编码能力，同时也能够加深对于算法的理解。  
在这个工程中，我将记录我研读caffe源代码的一些心得和注解。

## installation
caffe的安装方法，有很多教程，官网上也给出了安装方法。这里我给出一些建议，推荐在ubuntu系统上进行安装，这样会更简单，不会遇到太多复杂的问题。  
1.安装依赖  
caffe运行依赖于很多第三方的库，这些依赖需要提前安装  
```
# git
sudo apt-get install git

# protobuffer,leveldb,snappy,opencv,hdf5
sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler

# boost library
sudo apt-get install --no-install-recommends libboost-all-dev

# atlas library
sudo apt-get install libatlas-base-dev

# python dev
sudo apt-get install python-dev

# flags,glog,lmdb
sudo apt-get install libgflags-dev libgoogle-glog-dev liblmdb-dev
```
2.安装caffe  
建议使用cmake对caffe进行编译安装。在多次安装caffe的经验中，这样是最简单的且不容易出错。
详情请参考：http://caffe.berkeleyvision.org/installation.html

## protobuffer
protobuffer是由谷歌研发的对象序列化和反序列化的开源工具，是一种数据描述的工具，其功能类似于xml、json。但是protobuffer最终的数据描述文件是二进制的格式，这就造成了他阅读不直观，但是占用空间小，解析传输速度更快。首先编写描述定义文件proto，再通过protobuffer的编译器protoc对描述文件进行编译，得到可直接使用的二进制文件（支持C++、python、java）。例如，在C++代码中，会直接将demo.proto文件编译成可供代码直接使用的demo.pb.h和demo.pb.cc。  
在caffe中，blob定义、网络定义等都使用了protobuffer，使用者通过编写网络定义proto文件控制caffe构建网络。  
详情请参考：https://developers.google.cn/protocol-buffers/
## blob
