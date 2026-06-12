---
title: "Gyachi webcam problem, ubuntu 10.04"
date: 2010-08-03
forum: General Help
---

### Post by ubu_lin on 2010-08-03
hello everybody,

I need help in configuring/compiling gyachi for my ubuntu lucid-i386.
I can get deb from repository, but I want to try to configure myself, as I want to learn this process.

I had configured and installed gyachi 1.2.10 successfully with this following parameters

./configure --enable-maintainer-mode --disable-plugin_gpgme

but my webcam is not working in this build
on starting my webcam, i m getting this following error..

An error occurred at ioctl VIDIOCSPICT. could not set camara properties.

Fata : video format not supported by grab device

Error while querying mmap-buffers.

my webcam is working on other softwares, and may be it is v4l2 type.

can anyone give me step by step process of how to configure, what parameters i should use to configure/compile succesfully inorder to make my webcam work properly.

thankyou

---

### Post by kasatmaya.wordpress.com on 2010-08-11
> **ubu_lin said:**
> hello everybody,

I need help in configuring/compiling gyachi for my ubuntu lucid-i386.
I can get deb from repository, but I want to try to configure myself, as I want to learn this process.

I had configured and installed gyachi 1.2.10 successfully with this following parameters

./configure --enable-maintainer-mode --disable-plugin_gpgme

but my webcam is not working in this build
on starting my webcam, i m getting this following error..

An error occurred at ioctl VIDIOCSPICT. could not set camara properties.

Fata : video format not supported by grab device

Error while querying mmap-buffers.

my webcam is working on other softwares, and may be it is v4l2 type.

can anyone give me step by step process of how to configure, what parameters i should use to configure/compile succesfully inorder to make my webcam work properly.

thankyou

it seems you have to install other dependencies files that support for running webcam.
follow this link [http://www.linuxdedicatedwarnet.com/OnlineChatSupportWebcam-Gyachi.html](http://www.linuxdedicatedwarnet.com/OnlineChatSupportWebcam-Gyachi.html) to fix this problem. i hope this is usefull for you.

---

### Post by ubu_lin on 2010-08-13
> **kasatmaya.wordpress.com said:**
> it seems you have to install other dependencies files that support for running webcam.
follow this link [http://www.linuxdedicatedwarnet.com/OnlineChatSupportWebcam-Gyachi.html](http://www.linuxdedicatedwarnet.com/OnlineChatSupportWebcam-Gyachi.html) to fix this problem. i hope this is usefull for you.

Thankyou for reply, I got it now, as u said, I need to install 'libv4l-dev' package before compiling to make my webcam work. Now its working, thankyou again.. :)

---

