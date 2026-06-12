---
title: "How do I increase memory usage for Linux on dual boot?"
date: 2012-07-06
forum: General Help
---

### Post by josh223 on 2012-07-06
Ok so I initially had vista on this computer, I installed linux. When setting up the dual boot I made it so Linux would only take up 20 gigs or so. Well now it's all used up and I do not know how to increase the total memory used by Linux. 

I have 500G ram and only used less than 100g with windows and the 20 on Linux so I should have plenty of space left.

---

### Post by PhantomTurtle on 2012-07-07
I'm guessing you mean Hard Drive space and not RAM. To do that just follow the instructions on this page - [http://askubuntu.com/questions/116351/increase-partition-size-on-which-ubuntu-is-installed]("http://askubuntu.com/questions/116351/increase-partition-size-on-which-ubuntu-is-installed").
> As a matter of fact, you CAN enlarge the root filesystem while Ubuntu is running (I learned this recently myself here) - this sounds incredible but it's true :)

The magic command is resize2fs. From man resize2fs:

The resize2fs program will resize ext2, ext3, or ext4 file systems. It can be used to enlarge or shrink an unmounted file system located on device. If the filesystem is mounted, it can be used to expand the size of the mounted filesystem, assuming the kernel supports on-line resizing. (As of this writing, the Linux 2.6 kernel supports on-line resize for filesystems mounted using ext3 and ext4.).

My understanding is that gparted would use resize2fs behind the scenes anyway, so if for any reason booting from Ubuntu LiveCD is not an option, using resize2fs will solve the problem

> You are almost there.
You can not resize the partition using GParted while Ubuntu is running.
You will need to attach the GParted ISO's as a CD to the VM machine and reboot the machine so that the GParted will be loaded instead of Ubuntu (I think you can boot from the virtual CD by pressing F12 immediately after machine is started).
Once you booted into GParted the option to move/resize will be enabled as Ubuntu is not currently running.

---

