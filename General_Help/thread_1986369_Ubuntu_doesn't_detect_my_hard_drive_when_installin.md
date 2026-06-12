---
title: "Ubuntu doesn't detect my hard drive when installing"
date: 2012-05-24
forum: General Help
---

### Post by Silvu on 2012-05-24
Ubuntu was my first Linux distro ever, and this was only a few months ago.

While I don't think that I'm going to install Ubuntu on my computer, there are a few Ubuntu-based distros that I'd like to try and install (Hybryde).

It doesn't seem to detect my hard drive *at all* when trying to install it.

My computer is an Acer Aspire M3410-UR21P

I currently use Fedora Linux on it, so it's not the hard drive not working.

---

### Post by wilee-nilee on 2012-05-24
> **Silvu said:**
> Ubuntu was my first Linux distro ever, and this was only a few months ago.

While I don't think that I'm going to install Ubuntu on my computer, there are a few Ubuntu-based distros that I'd like to try and install (Hybryde).

It doesn't seem to detect my hard drive *at all* when trying to install it.

My computer is an Acer Aspire M3410-UR21P



I currently use Fedora Linux on it, so it's not the hard drive not working.

Open gparted on the live Ubuntu cd and post a screen shot, if it shows the partitions.

---

### Post by Silvu on 2012-05-25
I don't have any screenshots, but Gparted does show partitions

---

### Post by garvinrick4 on 2012-05-25
You know I am really not sure of why. I do know that Fedora wants to use LVM at install
with their Anaconda installer. I have not used LVM or experimented with it. I am just posing 
this and bumping you up to front to see if you can get some help. I have got a machine I do not 
use much at all anymore and I will see if I can duplicate your problem,
I would like to know also what LVM in a partition scheme does.  Someone should chime in here though.
"oldfred" might just be able to answer your troubles if LVM is problem. He is a Mod in these Forums.

---

### Post by oldfred on 2012-05-25
Oldfred does not know LVM, but does know the driver is not in the normal desktop install.

You can add it with 

sudo apt-get install lvm2

Then you may see your Fedora partitions. Someone posted that if you create partitions in advance you can install Fedora without LVM, which sometimes may be better.

I think you have to have the alternative installer or server installer to have the LVM (and RAID) drivers.

---

### Post by garvinrick4 on 2012-05-25
> Someone posted that if you create partitions in advance you can install Fedora without LVM, which sometimes may be better.
This I have done before, installed Fedora without LVM, I always make my partitions before installing and it is a choice in Anaconda installer to use or not use LVM.

---

