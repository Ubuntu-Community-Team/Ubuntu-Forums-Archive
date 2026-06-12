---
title: "SliTaz GNU/Linux and Gparted Issues"
date: 2009-09-18
forum: General Help
---

### Post by Keith Fox on 2009-09-18
SliTaz is usually a small OS that runs off a LiveCD or USB, but I have installed it to my hard drive in a temporary fix to a major problem with Linux Mint.  Usually I use Mint, but like I said I'm having major problems I won't discuss in this thread.

The problem I am having with Gparted partition editor.  (See attached photo)  SDA3 gets error:  Unable to find mount point.  Unable to read the contents of this file system!  Because of this some operations may be unavailable.

Not quite sure why it is saying that.

Also I need to resize sda9, but I am not able to resize that partition.  My unallocated space seems to be under sda1, and everything else under sda2.  I don't know why this is, but it won't let me put any of that unallocated space onto partition 9 because it's seperate.  I don't know why that is, but there is only one (1TB) SATA drive on this machine, broken into several partitions.

---

### Post by Liolikas on 2009-09-18
sda9 looks like full try to mount and ckeck. Of course you can not resize full partition.

---

### Post by Keith Fox on 2009-09-18
sda9 has been formatted. still can't resize because the free space is stuck under sda1, and sda9 is under the arrow down for sda2.  why these are segregated, I'm not sure why it's like this because it's the same drive.
Still doesn't solve my problem for sda3.

I'm just trying to fix my Linux Mint.  It is capable of booting, but it goes into a command prompt and I am able to log in fine. but what happened to my Desktop GUI? i don't know how to get my mintDesktop back.

---

