---
title: "gparted won't start"
date: 2011-05-28
forum: General Help
---

### Post by evanct on 2011-05-28
I downloaded gparted [here]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/")

I used unetbootin to put it on a USB drive. I rebooted and selected the USB drive from my boot menu. The following appears:

```

****************************************************************
GParted.
Gnome Partition Editor.
http://gparted.sourceforge.net
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
****************************************************************

```

And that's it. It just sits there with a blinking cursor. It doesn't respond to keyboard input. Nothing happens until I reboot.

Help? I've tried using Tuxboot instead of unetbootin, but that fails to even make a bootable drive.

---

### Post by linuxinstalledfromhdd on 2011-05-28
You are going about this the hard way. Try creating a live bootable USB of Ubuntu 10.10.  Boot from that USB flash stick, and run gparted from within the Live Bootable stick of Ubuntu 10.10.  If gparted isn't installed at that point, you can quickly add it with your terminal

sudo apt-get install gparted

---

### Post by evanct on 2011-05-28
Um, how is that the easy way? Making an entire bootable Ubuntu install when I can just boot gparted? I've done this before.

---

### Post by evanct on 2011-05-28
Nevermind, I redid the whole process of mounting the iso on the usb drive and now it works.

---

### Post by linuxinstalledfromhdd on 2011-05-28
You are cutting corners alittle bit though. It would be better to have a full bootable live USB stick of Ubuntu, and then when you have booted your system from the live stick of Ubuntu then you add anything you need later to it from the terminal:

sudo apt-get install gparted

Horse before the cart my friend. :)

You save yourselves some effort, but you are here with problems instead. See?

Try another method.

---

