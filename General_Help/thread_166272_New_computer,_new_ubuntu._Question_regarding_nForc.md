---
title: "New computer, new ubuntu. Question regarding nForce"
date: 2006-04-26
forum: General Help
---

### Post by phoenixy on 2006-04-26
Just got this new PC

[http://www.gateway.com/home/products/ret/ret_gt5056.shtml](http://www.gateway.com/home/products/ret/ret_gt5056.shtml)

5.10 Installation stopped at the Xserver part. So I went to look for nvidia linux motherboard and graphic driver. I found these from nVidia
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

The computer has AMD64 CPU. But my ubuntu 5.10 is non AMD64. Does that mean the IA32 nForce driver package is the one I should install? Anybody has any experience with nForce? Seems like I have to transfer these drivers to my new computer via a CD, since ethernet is down and the computer doesn't have a floppy drive.

---

### Post by twigboy on 2006-04-26
I have an nForce4 board with an amd64 x2 chip and I didnt need any additional drivers when installing ubuntu and it didnt stop at any point.  I did have to change the graphics driver to vesa instead of nv though.

---

### Post by phoenixy on 2006-04-26
lucky you, I wish my ethernet works so that I can run update and solve a whole lot of other problems:( 


Running into some problems with NFORCE-Linux-x86-1.0-0310-pkg1.run (Nvidia nForce driver):

1. first it says no precompiled kernel interface was found, the installer need to compile a new kernel interface (I select OK)

2. Then it says it cannot find the kernel source, so I
sudo apt-get install build-essential linux-headers-`uname -r`

3. Then I started again, with the command line option "kernel source path" set to "/usr/src/linux-headers-2.6.129-386. Now a warning pops up and says gcc-version-check failed. I'm running 4.0 while the kernel was compiled with 3.4 (I select go on) 

4. Then it builds the nvnet.ko kernel module, and it fails to load. The /var/log/nvidia-nforce-installer.log has the following shows the compilation process. In the end, it says

"done
kernel module compilation complete
Testing kernel module
Error: unable to load the kernel module 'nvnet.ko'. This is most likely because the kernel module was built using the wrong kernel source files...."


So, I guess there are two possible causes: 1. gcc is too new. 2. I really do have the wrong kernel src. 

How should I approach this problem?

---

### Post by phoenixy on 2006-04-26
I tried to change my cc 3.4 by running the following commands before running the nvidia script

CC=gcc-3.4
export CC

now it complains that gcc-3.4 cannot be found

But I found this gem
[http://www.ubuntuforums.org/archive/index.php/t-79896.html](http://www.ubuntuforums.org/archive/index.php/t-79896.html)

Now the installation completes

---

### Post by phoenixy on 2006-04-26
To sum up

modprobe nvnet

add this lines to /etc/network/interfaces

iface eth0 inet dhcp


Network up and functional, cheers:)

---

