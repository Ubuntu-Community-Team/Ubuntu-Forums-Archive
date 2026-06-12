---
title: "Partition USB Drive"
date: 2006-03-05
forum: General Help
---

### Post by Mau on 2006-03-05
Hi guys,
I have a ~239GB USB hard drive that I use for backups.  It is currently formatted as one giant NTFS partition.

I would like to partition this drive and format one partition to FAT32, another ext3, and keep my current NTFS partition.  What is the best way to do this?  Do I need to use the live CD, even though it's external?

Thanks,

---

### Post by andrewsawyer on 2006-03-05
Personally, if you want to reduce the size of an NTFS partition, I would do this from within Windows.  Although Linux is supposed to be able to read and write to an NTFS partition, I wouldn't trust it to resize one.

---

### Post by bikeboy on 2006-03-05
Grab a livecd such as gpartedcd or UBCD if you can. UBCD is windows based so it's good for ntfs stuff. Gparted is great for the rest of the partitioning stuff.

Ubuntu should be fine for shrinking ntfs, it does it in the install process if you want it to. But it's always best practice to back up important things anyway.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
[http://www.ubcd4win.com/](http://www.ubcd4win.com/)

---

### Post by Mau on 2006-03-05
[quote=bikeboy]Grab a livecd such as gpartedcd or UBCD if you can. UBCD is windows based so it's good for ntfs stuff. Gparted is great for the rest of the partitioning stuff.

Ubuntu should be fine for shrinking ntfs, it does it in the install process if you want it to. But it's always best practice to back up important things anyway.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")
[http://www.ubcd4win.com/]("http://www.ubcd4win.com/")[/quote]

I think I'll try to use GParted just for the sake of learning.  This drive just contains backup information that I already have.

So, how do I burn a bootable CD with Kubuntu?  :???:

---

### Post by bikeboy on 2006-03-05
[QUOTE=Mau]
So, how do I burn a bootable CD with Kubuntu?  :???:[/QUOTE]

Kubuntu should have K3b. Open it up, go to Tools > Burn CD Image, browse to the iso and click Start.

---

### Post by plors on 2006-03-06
gparted also does ntfs. You get the best results if you run it on its own [livecd]("http://gparted.sourceforge.net/livecd.php")

have fun

---

### Post by aysiu on 2006-03-06
If it's external, there's no reason to use a live CD--just make sure it's unmounted (but still plugged in).

---

### Post by Mau on 2006-03-09
I am using an external hard drive, and I cannot figure out how to get K3B to work (it always just spits out errors).

Anyways, I apt-getted GParted, and I started it up as root.  But when I select my external drive (sba), all the options are grayed out??  Partitioning was easy with the installer, but I never thought it would be so complicated after I've installed.  :p

---

### Post by plors on 2006-03-10
mau, which version of gparted do you use?
Can you provide us with a screenshot of this 'grey situation' (using gparted)?

thanks!

---

