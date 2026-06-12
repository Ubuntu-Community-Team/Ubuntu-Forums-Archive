---
title: "What is the latest 11.04 kernel version?"
date: 2011-08-25
forum: General Help
---

### Post by vincedba on 2011-08-25
Hi All,

I just installed Ubuntu 11.04 with kernel 2.6.38-8-generic.  I found in the internet there is kernel version 2.6.39-0 and I would like to update the kernel to this version.

I've added the repo ppa:kernel-ppa/ppa but It's not showing or can't find the kernel 2.6.39-0

E: Unable to locate package linux-headers-2.6.39-0
E: Couldn't find any package by regex 'linux-headers-2.6.39-0'
E: Unable to locate package linux-headers-2.6.39-0-generic
E: Couldn't find any package by regex 'linux-headers-2.6.39-0-generic'
E: Unable to locate package linux-image-2.6.39-0-generic
E: Couldn't find any package by regex 'linux-image-2.6.39-0-generic'



Please help. Why I can't see the kernel 2.6.39-0, am I missing some steps?


Thanks

---

### Post by WikedX on 2011-08-25
If you are going to upgrade kernels why wouldn't you install 3.0.3?

---

### Post by vincedba on 2011-08-25
> **WikedX said:**
> If you are going to upgrade kernels why wouldn't you install 3.0.3?


Can you please guide me how to do that? or any links ?


The most recent kernel I can see from apt-cache showpkg linux-headers is 2.6.38-11


Please help

---

### Post by kpike on 2011-08-25
My current kernel is 2.6.38-11. What are the advantages of upgrading to 3.0.3?

---

### Post by critin on 2011-08-25
I don't mean to steal the thread, but I'm interested to learn-- what is the benefit of changing from the default kernel?  

critin

---

### Post by vincedba on 2011-08-25
in some sites I found

"One post mentioned the issue of a bad interaction between [Unity]("http://addictivetips.com/tag/unity-2d"), the GL driver and the kernel, which often hangs the system. Updating the default 2.6.38-8 kernel can resolve such issues"


That is why I would like to update to the latest and stable kernel

---

### Post by WikedX on 2011-08-25
Download the newest stable kernel from kernel.org

Extract it to /usr/src/

System link it to a directory called /usr/src/linux

Enter the linux directory and type
make clean
make mrproper
Then copy your config file from /boot/ to the linux folder and rename it to .config

Then type make menuconfig
This brings up a menu
Scroll to the bottom and hit load alt config, and select .config

Then save and exit
After that just run 
make all
make modules_install
make install

[http://www.youtube.com/watch?v=bH4H9cHPV2s](http://www.youtube.com/watch?v=bH4H9cHPV2s)

---

### Post by ptn107 on 2011-08-25
If you want the latest supported Ubuntu kernel, steal it from oneiric.

32-bit
_[linux-headers-3.0.0-9_3.0.0-9.14_all.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.0.0-9_3.0.0-9.14_all.deb")_
_[linux-headers-3.0.0-9-generic_3.0.0-9.14_i386.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.0.0-9-generic_3.0.0-9.14_i386.deb")_
_[linux-image-3.0.0-9-generic_3.0.0-9.14_i386.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.0.0-9-generic_3.0.0-9.14_i386.deb")_

64-bit
_[linux-headers-3.0.0-9_3.0.0-9.14_all.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.0.0-9_3.0.0-9.14_all.deb")_
_[linux-headers-3.0.0-9-generic_3.0.0-9.14_amd64.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.0.0-9-generic_3.0.0-9.14_amd64.deb")_
_[linux-image-3.0.0-9-generic_3.0.0-9.14_amd64.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.0.0-9-generic_3.0.0-9.14_amd64.deb")_

Install them via the command line or software center.

---

### Post by VanR on 2011-08-26
I'm running 3.0.0-0300 on 11.04 because it's the only kernel I've used that mutes my PC speakers when I plug my headphones in the front of my computer. Didn't have this until 3.0.0-0300 and the kernels I've tried above that seem to have lost that ability on my machine. Don't know why though. To install 3.0 on Natty you will need another file though. I'll have to search here to find what that file is though.

This
[https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1](https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1)

---

### Post by Megaptera on 2011-08-26
> **ptn107 said:**
> If you want the latest supported Ubuntu kernel, steal it from oneiric.

32-bit
_[linux-headers-3.0.0-9_3.0.0-9.14_all.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.0.0-9_3.0.0-9.14_all.deb")_
_[linux-headers-3.0.0-9-generic_3.0.0-9.14_i386.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.0.0-9-generic_3.0.0-9.14_i386.deb")_
_[linux-image-3.0.0-9-generic_3.0.0-9.14_i386.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.0.0-9-generic_3.0.0-9.14_i386.deb")_

64-bit
_[linux-headers-3.0.0-9_3.0.0-9.14_all.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.0.0-9_3.0.0-9.14_all.deb")_
_[linux-headers-3.0.0-9-generic_3.0.0-9.14_amd64.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.0.0-9-generic_3.0.0-9.14_amd64.deb")_
_[linux-image-3.0.0-9-generic_3.0.0-9.14_amd64.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.0.0-9-generic_3.0.0-9.14_amd64.deb")_

Install them via the command line or software center.

I've never tried this before, so does Gdebi handle that or is there more to it? (I suspect it's more complicated!) Also, does it have to be done in a particular order?

Thanks. :D

---

### Post by thatguruguy on 2011-08-26
> **vincedba said:**
> in some sites I found

"One post mentioned the issue of a bad interaction between [Unity]("http://addictivetips.com/tag/unity-2d"), the GL driver and the kernel, which often hangs the system. Updating the default 2.6.38-8 kernel can resolve such issues"


That is why I would like to update to the latest and stable kernel

Link, please.

---

### Post by VanR on 2011-08-26
> **Megaptera said:**
> I've never tried this before, so does Gdebi handle that or is there more to it? (I suspect it's more complicated!) Also, does it have to be done in a particular order?

Thanks. :D

I just download them and use gdebi to install. I Install in this order.

the linux headers all-deb file
linux headers
linux kernel image

edit: just like he has them in his post.

---

### Post by garvinrick4 on 2011-08-26
You have got to upgrade module-init-tools first to go to 3.0 and up in Natty or Maverick.
Choose your architecture 32 or 64 bit in built files then next page take the .deb and
download and then just click on and will install thru Ubuntu software center.
Do this before installing image of 3.0 or up.

[https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1](https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1)

Always look for built files first for anything you want to install .deb
Here is all kernels in built.
[Index of /~kernel-ppa/mainline]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

---

### Post by Megaptera on 2011-08-26
Thanks VanR and garvinrick4.

---

### Post by Duncan Williams on 2011-08-26
Does the kernel update still break nvidia drivers?
I am wary of doing a kernel update for this reason.
current kernel:   2.6.38-10-generic

---

### Post by elliotn on 2011-08-26
I will wait till the official kernel 3 comes to 11.04

---

### Post by kpike on 2011-08-26
When you update kernels, are all your settings from the previous kernel imported? If not, can I use deja dup to restore?

---

### Post by snowpine on 2011-08-26
> **elliotn said:**
> I will wait till the official kernel 3 comes to 11.04

It will never happen. Ubuntu is not "rolling release" and 11.04 will always give you the 2.6.38 kernel by default.

---

### Post by dino99 on 2011-08-26
> **kpike said:**
> When you update kernels, are all your settings from the previous kernel imported? If not, can I use deja dup to restore?

no need to worry about settings, yours will be applied

---

