---
title: "can I do anything to speed up ubuntu running off usb"
date: 2011-06-16
forum: General Help
---

### Post by planet pluto on 2011-06-16
I am running Ubuntu 11.04 off of an 8GB flash drive. I have no hard disks but I do have a 3.2 GHz Pentium 4 with Hyperthreading and 1 GB of RAM. So, it shouldn't be my system that is causing it to run slow, but rather limitations of the USB (I'm pretty sure it's USB 2.0). Is there anything I can do, unnecessary processes I can kill, etc. to make it run faster?

---

### Post by 23dornot23d on 2011-06-16
Do you use Ubuntuone .... Tomboy Notes or Banshee ?

If not the following might give you a little better response time ....

Go into synaptic package manager and remove anything you see to do with ubuntuone
I found this slows down exit from the desktop mainly but if you use ubuntuone .... then
obviously keep it ..... 

Mono .... is a massive set of packages on the system - removing this may give you some
free space back ..... and it can be replaced for the notes with gnote - again looking in
synaptic package manager you will see all the entries for mono ..... its up to you as this
also affects Banshee ...... which I replace with Streamtuner .... which is in the repositories
and if you search using the Synaptic package manager will find its there.

If they make no difference .... you could just add them back using Synaptic again .... 

Hope that this helps in some small way ......

( Update ..... I am only advising this for users with Flash drives and limited resources .....)

---

### Post by Herman on 2011-06-16
[LIST]
[*]select Ubuntu Classic with No Effects at login
[*]modify grub to boot your kernel with the noop or deadline IO scheduler
[*]install localepurge to reduce occupied disk space by only allowing locales you need.
[*]adjust swappiness to tell your system to heavily favor the use of memory and limit its tendency to write to the swap area.
[*]align your ext4 file system to the flash memory erase blocks with tune2fs
[/LIST]
You should also install with no swap area and install dynamic swap space manager instead, that should help you optimize your available disk space and help in lots of other ways.

Optimizing the use of available disk space is important because the ext series file systems need no defragging while disk usage is less than about 80%. You will obviously need files, and by reducing the operating system's disk footprint you leave more room for your files without exceeding 80%. 
From a hardware point of view also, the more spare room you have the better so the flash controller can rotate writes to disk across more empty blocks.

Some flash memory sticks don't have any cache like most hard disks do (a small amount of RAM for queuing up small writes to disk in until the device has time to catch up), as most of them are only designed for data storage and transfer and not for running an operating system in. Also they may have a slow method in the controller for erasing old used blocks ready for the next disk write. If you are unlucky your chosen make and model of USB flash memory stick could be a slow one, and in that case you will experience long pauses like the operating system keeps freezing up and works only in fits and starts. 
If you are lucky, you can have a flash memory stick with some kind of faster controller and a memory cache and it will work almost as smoothly as a hard disk and will run Ubuntu quite well. So if you try everything and still aren't happy, maybe try a different model or switch to a different USB flash memory stick manufacturer.

 The speed of the USB2 interface is a lot slower than through IDE or SATA, and that limits the speed you can achieve too. USB3 devices are starting to appear and will be great for SSDs.

---

### Post by cbowman57 on 2011-06-16
Other great suggestions already but you might benefit from installing to the usb using btrfs as your file system, though you will still need a small /boot partition created with anything but btrfs.  Btrfs is supposed to be optimized a little better for SSD, should extend to a flash drive.  Also gives you the option of using on the fly compression, which might provide a little extra speed.

It's been my experience though that installing to usb stick is slow.  I think it's a little quicker to just use a live image &  persistence since the live mode loads to RAM, but that's just my opinion.

---

### Post by C.S.Cameron on 2011-06-16
Following link to running ubuntu in RAM.

[http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694)

---

