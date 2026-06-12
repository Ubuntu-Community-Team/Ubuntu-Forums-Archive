---
title: "Using GParted to resize primary partition"
date: 2011-07-15
forum: General Help
---

### Post by palacealex on 2011-07-15
Hi

I am currently running 11.04 as the sole OS on my laptop but I am looking to dual boot with windows 7 as well.  When I tried to install 7 I found that neither of my partitions were off the correct file system to install on.

I did some research and found that GParted was the software to use so I installed and tried to make alterations to my partitions.  However I have found my options to be limited which I believe to be because my main partition is currently mounted and this is the one that needs to be altered.

I am not sure what to do next, any help would be greatly appreciated

Thanks

---

### Post by szal on 2011-07-15
***polishes his crystal ball*** Use GParted live CD…

---

### Post by ~!geek!~ on 2011-07-15
Yeah, just boot the live cd or usb. Gparted is already there. I believe this is the software that you use while installing ubuntu for hard-disk partition which is removed at the last stage of installation. So just boot with live cd. Run ubuntu without installing it and type command sudo gparted on terminal.

---

### Post by dandnsmith on 2011-07-15
You'll find it as a menu item under System|Admin, probably, and yes, you need to run from something which doesn't have the partitions 'in use'

---

### Post by Mark Phelps on 2011-07-15
To explain what folks are telling you ...

In order to change the properties of a partition, it must be "unmounted" (i.e., NOT in use).  But, to run from an OS contained in a partition, it must be "mounted".

So, this means you can NOT make any changes to partitions that you are using.

Thus, you have to boot from a CD containing the software needed to do partition management.  The Ubuntu LiveCD contains GParted (Gnome Partition Editor), as does the GParted LiveCD (which you can download from distrowatch.com).

So basically, you do the following:
1) Boot from the CD
2) Run GParted
3) Make the partition changes
4) Reboot -- without the CD insterted

---

