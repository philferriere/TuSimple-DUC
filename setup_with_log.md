## Setup

> Note: `\\naspro\devt\Datasets\TuSimple-DUC` has pretrained models

1. Clone the repository:

```shell
git clone git@github.com:TuSimple/TuSimple-DUC.git
cd TuSimple-DUC
python setup.py develop --user
```

Log:

```shell
(dlwin27) pferr@MSI E:\repos
$ git clone https://github.com/TuSimple/TuSimple-DUC.git
Cloning into 'TuSimple-DUC'...
remote: Counting objects: 49, done.
remote: Compressing objects: 100% (13/13), done.
remote: Total 49 (delta 6), reused 12 (delta 3), pack-reused 32
Unpacking objects: 100% (49/49), done.

(dlwin27) pferr@MSI E:\repos
$ cd TuSimple-DUC

(dlwin27) pferr@MSI E:\repos\TuSimple-DUC-wip-setup
$ python setup.py develop --user
running develop
running egg_info
creating tusimple_duc.egg-info
writing requirements to tusimple_duc.egg-info\requires.txt
writing tusimple_duc.egg-info\PKG-INFO
writing top-level names to tusimple_duc.egg-info\top_level.txt
writing dependency_links to tusimple_duc.egg-info\dependency_links.txt
writing manifest file 'tusimple_duc.egg-info\SOURCES.txt'
reading manifest file 'tusimple_duc.egg-info\SOURCES.txt'
writing manifest file 'tusimple_duc.egg-info\SOURCES.txt'
running build_ext
Creating c:\users\pferr\appdata\roaming\python\python27\site-packages\tusimple-duc.egg-link (link to .)
Adding tusimple-duc 1.0.0 to easy-install.pth file

Installed e:\repos\tusimple-duc-wip-setup
Processing dependencies for tusimple-duc==1.0.0
Searching for Pillow==4.2.1
Best match: Pillow 4.2.1
Adding Pillow 4.2.1 to easy-install.pth file

Using e:\toolkits.win\anaconda3-4.4.0\envs\dlwin27\lib\site-packages
Searching for numpy==1.13.1
Best match: numpy 1.13.1
Adding numpy 1.13.1 to easy-install.pth file

Using e:\toolkits.win\anaconda3-4.4.0\envs\dlwin27\lib\site-packages
Searching for configparser==3.5.0
Best match: configparser 3.5.0
Adding configparser 3.5.0 to easy-install.pth file

Using e:\toolkits.win\anaconda3-4.4.0\envs\dlwin27\lib\site-packages
Searching for olefile==0.44
Best match: olefile 0.44
Adding olefile 0.44 to easy-install.pth file

Using e:\toolkits.win\anaconda3-4.4.0\envs\dlwin27\lib\site-packages
Finished processing dependencies for tusimple-duc==1.0.0
```

2. Download the pretrained model from [Google Drive](https://drive.google.com/open?id=0B72xLTlRb0SoREhISlhibFZTRmM).

3. Clone and Build MXNet (only tested on the TuSimple version):

```shell
git clone --recursive https://github.com/TuSimple/mxnet.git
cd mxnet
make -j8
cd python
python setup.py develop --user
```

For more MXNet tutorials, please refer to the [official documentation](https://mxnet.incubator.apache.org/install/index.html).

Unfortunately, the information above does not work for Windows. For Windows, we need to follow MXNet's build instructions [here](http://mxnet.incubator.apache.org/get_started/windows_setup.html):

![](img/mxnet.png)

To build and install MXNet yourself, you need the following dependencies. Install the required dependencies:

1. If Microsoft Visual Studio 2013 is not already installed, download it from [here](https://my.visualstudio.com/Downloads?q=visual%20studio%202013&wt.mc_id=o~msft~vscom~older-downloads). Choose the following version:

![](img/vs2013download.png)

2. Install the Visual C++ Compiler by running `en_visual_studio_community_2013_with_update_5_x86_6816332.exe`. Choose your favorite folder (ours: `E:\toolkits.win\vs2013`):

![](img/vs2013setup1.png)

None of the optional features need to be installed for this project:

![](img/vs2013setup2.png)

3. Back up all of the files in the C:\Program Files (x86)\Microsoft Visual Studio 12.0\VC folder to a different location.

4. Copy all of the files in the C:\Program Files (x86)\Microsoft Visual C++ Compiler Nov 2013 CTP folder (or the folder where you extracted the zip archive) to the C:\Program Files (x86)\Microsoft Visual Studio 12.0\VC folder, and overwrite all existing files.

5. Download [OpenCV](http://sourceforge.net/projects/opencvlibrary/files/opencv-win/3.0.0/opencv-3.0.0.exe/download)'s self-extracting archive.

6. Unzip the OpenCV package to `E:\toolkits.win\opencv-3.0.0`

7. Set the environment variable `OpenCV_DIR` to point to `E:\toolkits.win\opencv-3.0.0`.

8. If you don’t have the Intel Math Kernel Library (MKL) installed, download and install OpenBlas.

9. Set the environment variable `OpenBLAS_HOME` to point to the OpenBLAS directory that contains the include and lib directories. Typically, you can find the directory in `C:\Program files (x86)\OpenBLAS\`.

10. Download and install [CuDNN](https://developer.nvidia.com/cudnn). To get access to the download link, register as an NVIDIA community user.

After you have installed all of the required dependencies, build the MXNet source code:

1. [SKIP THIS STEP AS THEY USE THEIR OWN VERSION OF MXNET] Download the MXNet source code from GitHub.

2. Use [CMake](https://cmake.org/) to create a Visual Studio solution in ./build.

3. In Visual Studio, open the solution file,.sln, and compile it. These commands produce a library called mxnet.dll in the ./build/Release/ or ./build/Debug folder.

Next, we install graphviz library that we use for visualizing network graphs you build on MXNet. We will also install Jupyter Notebook used for running MXNet tutorials and examples.
Install graphviz by downloading MSI installer from Graphviz Download Page. Note Make sure to add graphviz executable path to PATH environment variable. Refer here for more details
Install Jupyter by installing Anaconda for Python 2.7 Note Do not install Anaconda for Python 3.5. MXNet has few compatibility issue with Python 3.5.
We have installed MXNet core library. Next, we will install MXNet interface package for programming language of your choice:

Log:

```shell
(dlwin27) pferr@MSI E:\repos\TuSimple-DUC-wip-setup
$ git clone --recursive https://github.com/TuSimple/mxnet.git
Cloning into 'mxnet'...
remote: Counting objects: 46829, done.
remote: Total 46829 (delta 0), reused 0 (delta 0), pack-reused 46829
Receiving objects: 100% (46829/46829), 20.38 MiB | 6.81 MiB/s, done.
Resolving deltas: 100% (29576/29576), done.
Submodule 'cub' (https://github.com/dmlc/cub.git) registered for path 'cub'
Submodule 'dlpack' (https://github.com/dmlc/dlpack) registered for path 'dlpack'
Submodule 'dmlc-core' (https://github.com/dmlc/dmlc-core.git) registered for path 'dmlc-core'
Submodule 'mshadow' (https://github.com/dmlc/mshadow.git) registered for path 'mshadow'
Submodule 'nnvm' (https://github.com/dmlc/nnvm) registered for path 'nnvm'
Submodule 'ps-lite' (https://github.com/dmlc/ps-lite) registered for path 'ps-lite'
Cloning into 'E:/repos/TuSimple-DUC-wip-setup/mxnet/cub'...
remote: Counting objects: 190, done.
remote: Total 190 (delta 0), reused 0 (delta 0), pack-reused 190
Receiving objects: 100% (190/190), 498.22 KiB | 2.50 MiB/s, done.
Resolving deltas: 100% (58/58), done.
Cloning into 'E:/repos/TuSimple-DUC-wip-setup/mxnet/dlpack'...
remote: Counting objects: 124, done.
remote: Compressing objects: 100% (12/12), done.
remote: Total 124 (delta 5), reused 13 (delta 3), pack-reused 104
Receiving objects: 100% (124/124), 50.67 KiB | 2.81 MiB/s, done.
Resolving deltas: 100% (39/39), done.
Cloning into 'E:/repos/TuSimple-DUC-wip-setup/mxnet/dmlc-core'...
remote: Counting objects: 4481, done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 4481 (delta 0), reused 2 (delta 0), pack-reused 4476
Receiving objects: 100% (4481/4481), 1.02 MiB | 4.14 MiB/s, done.
Resolving deltas: 100% (2654/2654), done.
Cloning into 'E:/repos/TuSimple-DUC-wip-setup/mxnet/mshadow'...
remote: Counting objects: 4500, done.
remote: Total 4500 (delta 0), reused 0 (delta 0), pack-reused 4500
Receiving objects: 100% (4500/4500), 1.42 MiB | 4.91 MiB/s, done.
Resolving deltas: 100% (3089/3089), done.
Cloning into 'E:/repos/TuSimple-DUC-wip-setup/mxnet/nnvm'...
remote: Counting objects: 2728, done.
remote: Compressing objects: 100% (54/54), done.
remote: Total 2728 (delta 24), reused 45 (delta 23), pack-reused 2651
Receiving objects: 100% (2728/2728), 944.89 KiB | 3.25 MiB/s, done.
Resolving deltas: 100% (1537/1537), done.
Cloning into 'E:/repos/TuSimple-DUC-wip-setup/mxnet/ps-lite'...
remote: Counting objects: 1910, done.
remote: Total 1910 (delta 0), reused 0 (delta 0), pack-reused 1910
Receiving objects: 100% (1910/1910), 582.61 KiB | 2.49 MiB/s, done.
Resolving deltas: 100% (1217/1217), done.
Submodule path 'cub': checked out '05eb57faa0a4cac37c2a86fdf4b4dc865a95a1a3'
Submodule path 'dlpack': checked out 'a6e09b58dc00ee0065f5b7879800e646fbb01d1e'
Submodule path 'dmlc-core': checked out '71bfbd3a946075cea66ca9e19bad86dd33c19b46'
Submodule path 'mshadow': checked out '497eb9180b24592b7332e7e08f2c053ec5346524'
Submodule path 'nnvm': checked out 'bcfbf903429d086f16b19b4d202788de06e45536'
Submodule 'dmlc-core' (https://github.com/dmlc/dmlc-core) registered for path 'nnvm/dmlc-core'
Submodule 'plugin/nnvm-fusion' (https://github.com/dmlc/nnvm-fusion.git) registered for path 'nnvm/plugin/nnvm-fusion'
Cloning into 'E:/repos/TuSimple-DUC-wip-setup/mxnet/nnvm/dmlc-core'...
remote: Counting objects: 4481, done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 4481 (delta 0), reused 2 (delta 0), pack-reused 4476
Receiving objects: 100% (4481/4481), 1.02 MiB | 4.33 MiB/s, done.
Resolving deltas: 100% (2654/2654), done.
Cloning into 'E:/repos/TuSimple-DUC-wip-setup/mxnet/nnvm/plugin/nnvm-fusion'...
remote: Counting objects: 24, done.
remote: Total 24 (delta 0), reused 0 (delta 0), pack-reused 24
Submodule path 'nnvm/dmlc-core': checked out 'a2999eec6c6bbb7a484dea7c3dd652772969585d'
Submodule path 'nnvm/plugin/nnvm-fusion': checked out '86853a73e93fdbcdaec6fd3eda39e8f11d554c92'
Submodule path 'ps-lite': checked out 'acdb698fa3bb80929ef83bb37c705f025e119b82'

(dlwin27) pferr@MSI E:\repos\TuSimple-DUC-wip-setup
$ cd mxnet

```

3. Training:

```shell
cd train
python train_model.py ../configs/train/train_cityscapes.cfg
```

The paths/dirs in the ``.cfg`` file need to be specified by the user.

4. Testing

```
cd test
python predict_full_image.py ../configs/test/test_full_image.cfg
```

The paths/dirs in the ``.cfg`` file need to be specified by the user.

5. Results:

Modify the ``result_dir`` path in the config file to save the label map and visualizations. The expected scores are:

(single scale testing denotes as 'ss' and multiple scale testing denotes as 'ms')

- ResNet101-DUC-HDC on CityScapes testset (mIoU): 79.1(ss) / 80.1(ms)
- ResNet152-DUC on VOC2012 (mIoU): 83.1(ss)
