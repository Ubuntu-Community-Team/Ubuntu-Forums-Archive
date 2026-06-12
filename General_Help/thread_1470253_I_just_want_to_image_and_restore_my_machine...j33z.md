---
title: "I just want to image and restore my machine...j33z!"
date: 2010-05-02
forum: General Help
---

### Post by 98cwitr on 2010-05-02
So I've used Clonezilla and partimg to image my machine...great I can take the image, but the really annoying part is that it HAS to be the same size HD in order to lay the image back down. I want to take an image and when I get my SSD in, lay the image down...but I have a 500GB HD and will not be getting a 500GB SSD. Can someone recommend a way to do this...maybe I'm just using the programs incorrectly?

---

### Post by 98cwitr on 2010-05-02
bump...forums are rolling today aren't they ;)

---

### Post by mk1w86 on 2010-05-02
You could just copy the contents of the partition(s) you are trying to take an image of instead.  You would then create the partitions you want on your SSD and copy your data to the corresponding partition(s). ;)

If you are trying to copy a Ubuntu installation you will need to install Grub to the SSD.  If you are using a fresh install of Ubuntu 9.10 or later follow this guide:

[https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2](https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2)

---

### Post by 98cwitr on 2010-05-02
will that keep all my menu items in place too?

---

### Post by mk1w86 on 2010-05-02
> **98cwitr said:**
> will that keep all my menu items in place too?

I'm not quite sure what you mean, your Gnome menu on your desktop or your Grub menu?  If the Gnome menu, yes, if your Grub menu, all the menu items will be recreated when you reinstall Grub but they should be the same. :-s

---

### Post by bumanie on 2010-05-02
You could shrink the partition before imaging and then image the shrunken partition, making sure it is the same size or smaller than the proposed ssd - also make sure that the amount of data held on your present hard drive does not exceed the ssd's size. You can use gparted to shrink the present hard drive filesystem, but it is not a quick process and does have some danger as far as if there is a power failure during shrinking, the filesystem will be completely wrecked. That is only a small chance of happening, but has happened. You need to do the shrinking from a live cd - either the ubuntu live cd or the dedicated gparted live cd

---

### Post by mk1w86 on 2010-05-02
98cwitr, you could start with my method (copying the files from your partition(s)) and then try bumanie's method and if that fails e.g. your filesystem get damaged because of a power cut as bumanie mentioned, you could then use my suggestion as a plan B. ;)

---

### Post by 98cwitr on 2010-05-03
I thought about that...I've got gparted on my sysrescuecd and could shrink the partition and then take an image of that part.

mk1, I was referring to Gnome, I know that my grub menu will be part of the boot process on the MBR...I would like to keep the version of grub I've got though, it's quick and doesn't display the list without prompting. Clonezilla will let me image the partition with the MBR thankfully.

The Live CD idea (copy the root dir to the new drive) seems like an idea, I will to install a baseline OS (Lucid) on it before doing this, right?

---

### Post by mk1w86 on 2010-05-03
> **98cwitr said:**
> The Live CD idea (copy the root dir to the new drive) seems like an idea, I will to install a baseline OS (Lucid) on it before doing this, right?

Well, no.  The root partition that is mounted at / *is* your installation.  After copying your installation (the contents of /) to the SSD you would then have to install grub to the MBR of your SSD so you can boot Ubuntu.  See my earlier post for more information on this.

Like I said in my previous post, it's is worth trying the partition resizing method first but after you have copied the contents of / to some sort of external storage as a backup. ;)

---

### Post by 98cwitr on 2010-05-11
...

---

### Post by 98cwitr on 2010-05-13
and fail 

[http://ubuntuforums.org/showthread.php?p=9292672#post9292672](http://ubuntuforums.org/showthread.php?p=9292672#post9292672)

---

### Post by 98cwitr on 2010-05-14
ok, shrunk the partition down to 26GB ext3, took an image with partimge, and laid the image back down on a 40GB drive (38GB ext4, 2GB swap, 0 extended). Lo and behold, I only have 26GB of usable space, but under disk utility it shows a healthy 38GB ext3 drive. How am I going to get all space to be usable?

---

### Post by Grenage on 2010-05-14
Can you not expand the partition using gparted?  Boot off a liveCD and run it there.

---

### Post by 98cwitr on 2010-05-15
gparted shows the drive as 38GB :? 
file system is 26.95 :?

am I going to need to set up a extended partition of my SSD?

all from live cd

Live CD:
[IMG]http://img.photobucket.com/albums/v673/98cwitr/hds.png?t=1273896892[/IMG]

HD:
[IMG]http://img.photobucket.com/albums/v673/98cwitr/hd.png[/IMG]

---

### Post by 98cwitr on 2010-05-18
SSD should be here tomorrow...really tempted just to do a fresh install and pull down the apps from APTonCD that I already have saved...and my email archive. What do ya'll think?

---

### Post by mk1w86 on 2010-05-19
> **98cwitr said:**
> SSD should be here tomorrow...really tempted just to do a fresh install and pull down the apps from APTonCD that I already have saved...and my email archive. What do ya'll think?

Personally, that is what I would do. ;)

I normally do a fresh Ubuntu install every 6 months or so anyway when a new Ubuntu version is released, it keeps my system clean because I often install a lot of packages I only use a couple of times.  All my data is on separate partitions so the process is fairly quick, probably quicker than doing an upgrade.

---

### Post by 98cwitr on 2010-05-19
fresh install...no aptoncd b/c I there were a lot of apps I really didnt need. Had everything installed and the way I wanted it in only about an hour :)

---

