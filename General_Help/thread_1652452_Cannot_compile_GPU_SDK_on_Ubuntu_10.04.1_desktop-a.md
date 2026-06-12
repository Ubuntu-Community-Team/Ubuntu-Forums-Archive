---
title: "Cannot compile GPU SDK on Ubuntu 10.04.1 desktop-amd64 (64bit)"
date: 2010-12-24
forum: General Help
---

### Post by romanpc on 2010-12-24
Hi,

I'm trying to compile samples from GPU SDK for CUDA. I have i7 Intel processor and two GTX 460.

I've installed following packages:
devdriver_3.2_linux_64_260.19.26.run
cudatoolkit_3.2.16_linux_64_ubuntu10.04.run
gpucomputingsdk_3.2.16_linux.run

I did all the tricks (add blacklist …) according to the links: 
[http://developer.download.nvidia.com/compute/cuda/3_2_prod/docs/Getting_Started_Linux.pdf](http://developer.download.nvidia.com/compute/cuda/3_2_prod/docs/Getting_Started_Linux.pdf)
[http://wiki.accelereyes.com/wiki/index.php/Installing_CUDA_Under_Ubuntu_10.04](http://wiki.accelereyes.com/wiki/index.php/Installing_CUDA_Under_Ubuntu_10.04)
[http://developer.nvidia.com/object/cuda_3_2_downloads.html](http://developer.nvidia.com/object/cuda_3_2_downloads.html)

The PATH and LD_LIBRARY_PATH=/usr/local/cuda/lib64:/usr/local/cuda/lib: are set. The latter in .bashrc and in /etc/ld.so.conf.d/cuda.conf.
 
I'm getting the following error during the "make" process: 
/usr/bin/ld: cannot find -lGLU
../../bin/linux/release/postProcessGL Error 1
The solution: sudo ln -s libGL.so.260.19.26 libGL.so does not help. 

If I do: sudo apt-get install freeglut3-dev I get error: Broken packages
The following packages have unmet dependencies:
freeglut3-dev: Depends: libgl1-mesa-dev but it is not going to be installed or libgl-dev
Depends: libglu1-mesa-dev but it is not going to be installed or libglu-dev

If I do: sudo apt-get install libgl1-mesa-dev
The following packages have unmet dependencies:
libgl1-mesa-dev: Depends: libgl1-mesa-glx(= 7.7.1-1ubuntu2) but 7.7.1-1ubuntu3 is to be installed

If I do: sudo apt-get install libgl1-mesa-glx
is already the newest version

I googled it and I've tried to install all kinds of packages and now just don't know what to do. I think I have dependency problem. 

Does anyone have any ideas how can I solve compilation problems?

Thanks

Roman

---

### Post by romanpc on 2010-12-25
Hi,

I have already got the solution from another forum: [http://forums.nvidia.com/index.php?showtopic=185941&st=0&p=1152916&#entry1152916](http://forums.nvidia.com/index.php?showtopic=185941&st=0&p=1152916&#entry1152916)

It was exactly what I needed. Now I was able to compile and to pass deviceQuery and bandwidth tests.   

Thanks,

Roman

---

