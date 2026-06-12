---
title: "How to repartition my harddrive"
date: 2012-03-27
forum: General Help
---

### Post by mjsilverstri on 2012-03-27
Hi,

I have ubuntu install on my hard drive. How can I edit the partition table (e.g. resize the current partition and create a smaller partition) when I only have 1 partition (which ubuntu is installed)?

---

### Post by PhantomTurtle on 2012-03-27
You can use a live cd or usb. Get a gparted live cd to resize the partition and create a new one. I'm not sure if the Ubuntu 11.10 live cd has gparted on it. You can get gparted live from the gparted site. Instructions: [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by Mark Phelps on 2012-03-27
The Ubuntu desktop CD does have GParted on it.

But ... you have to boot from CD because you can't make changes to a partition that is currently in use ... which is the case when you boot into Ubuntu that's on your hard drive.

---

### Post by ajgreeny on 2012-03-27
The live CD/USB you used to install already has gparted on it.

Boot to it and open gparted, then right click on the swap partition and choose swapoff, in case that interferes with anything you want to do (it may, it may not; depends on your partition layout).

You can then shrink the ubuntu partition preferably by dragging the right hand end to the left, and make a new partition with the empty space.  Later on after a reboot you can add a line to /etc/fstab to automount that partition at boot time.  Come back again if you need help with that.

The resizing may take a very long time, but whatever else you do, **do not stop it or interrupt it**, or you will probably corrupt the partition and not be able to boot.

---

