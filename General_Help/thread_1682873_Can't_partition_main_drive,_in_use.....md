---
title: "Can't partition main drive, in use...."
date: 2011-02-06
forum: General Help
---

### Post by warmnscsi on 2011-02-06
So I have my entire hard disk  formatted as ext 4 and now I would like to partition it so I can put  windows on it. I can't do it from the windows installer because windows  doesn't like to recognise linux formats. 

I've tried using Disk Utility, GParted, and KDE Partition Manager and  they all tell me I cant partition the main drive cause it is in use. I  don't have any access to live cd's or usb's. Does anyone know how I can  do a partition? I'm using ub10.10 btw. Thanks.

---

### Post by randiroo76073 on 2011-02-06
You'll need to download and burn a live cd, you can't repartition a mounted partition AFAIK

---

### Post by [Snc] on 2011-02-06
First you have to unmount the drive, this is simplest done from a live CD/USB

---

### Post by jroa on 2011-02-06
You can download a GParted live iso and burn to a cd here.  [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Then boot with the cd and make your changes.

---

### Post by ajgreeny on 2011-02-06
There is no need to download and burn another live CD if you already have a ubuntu live CD; gparted is there for you in System > Administration.

---

