---
title: "Run it with Windows"
date: 2011-12-03
forum: General Help
---

### Post by cwrann on 2011-12-03
I recently got a new laptop and chose to install Ubuntu on it using the "run it with Windows" option on the Ubuntu page. It installs Ubuntu with WUBI.

Are there any distinguishable cons to installing Ubuntu on my laptop in this manner rather than downloading to a disk or usb and installing it that way? Is it the same Ubuntu? Will it run slower than if I installed it in the traditional manner?

---

### Post by Basher101 on 2011-12-03
The only downsides are:

1. it runs a bit slower, but not slow enough for you to actually notice

and

2. if your Windows should get busted, you have nothing you can boot into to fix it nativeley

other than those i don't think there is any downside at all.

I should advise you though, if you consider to install it directly to your hard disk, inform yourself throughoutly on the forums and tutorials on how to install properly. I did rush my first install without reading much about it and ended up wiping windows...

---

### Post by cwrann on 2011-12-03
Thank you, Basher101. Any ideas as to why it runs a little slower? It may be to a noticeable degree on my laptop. I 
I've been running nothing but Ubuntu on my Desktop for the last five years (since Dapper Drake) and the Desktop has always been super-fast. The specs on my Laptop are better than those on my Desktop. Then again the latest Ubuntu I have on the desktop is 10.04, is the eleven series slower in general? It seems to have a lot more bells and whistles.

---

### Post by Serpher on 2011-12-03
> **cwrann said:**
> Thank you, Basher101. Any ideas as to why it runs a little slower? It may be to a noticeable degree on my laptop. I 
I've been running nothing but Ubuntu on my Desktop for the last five years (since Dapper Drake) and the Desktop has always been super-fast. The specs on my Laptop are better than those on my Desktop. Then again the latest Ubuntu I have on the desktop is 10.04, is the eleven series slower in general? It seems to have a lot more bells and whistles.

Speed between distributions isn't an awful lot. Linux is so lightweight that even if 11.10 did run slower it would be so marginal you wouldn't notice since it's basically the same system. Also the slowness comes from it having to read an EXT4 filesystem in an NTFS filesystem. The minor slowdown comes from your hardrive, and chances are yours is no faster than anybody else.

---

### Post by Basher101 on 2011-12-03
> **Serpher said:**
> Speed between distributions isn't an awful lot. Linux is so lightweight that even if 11.10 did run slower it would be so marginal you wouldn't notice since it's basically the same system. Also the slowness comes from it having to read an EXT4 filesystem in an NTFS filesystem. The minor slowdown comes from your hardrive, and chances are yours is no faster than anybody else.

thats what i meant that you would not notice much the speed difference...

A dualboot is always nice to have in case one of your operating systems gets broken so you can fix it from the other. But again heed my warning, read yourself into the partition editing before doing anything rash. I learned it the hard way....


regards

---

### Post by cwrann on 2011-12-03
Thanks all, I think I will end up going with the dual boot, I just saw the new option and thought I'd give it a try. Thanks for the warning Basher101, I've actually been fooling around with partition editing for a few years now. Though my desktop is 100% Ubuntu, I like to keep the OS on a separate partition than everything else, this makes fresh installs of the latest versions of Ubuntu a snap.

---

### Post by Serpher on 2011-12-03
> **Basher101 said:**
> thats what i meant that you would not notice much the speed difference...

I wasn't disagreeing, only explaining as to why and where he would see those marginal slowdowns.

Seriously though I suggest installing it on it's own partition. It's more "clean" that way.

---

### Post by Basher101 on 2011-12-03
> **serpher said:**
> i wasn't disagreeing, only explaining as to why and where he would see those marginal slowdowns.

Seriously though i suggest installing it on it's own partition. It's more "clean" that way.

+1

---

### Post by cwrann on 2011-12-03
Defiantly installing it on it's own partition, something feels wrong about the WUBI method, maybe I'm just used to the old fashioned Ubuntu way. I will create a Windows partition (only because my scanner is not supported by Ubuntu) a partition for Ubuntu and then a large partition to mount the home folder into.

Thanks again!

---

### Post by Synoc on 2011-12-03
a note:
I don't know if  this is still a problem, if you want to share files between OS's, you might want to shrink the windows volume down to about twice what it takes to run it, plus some extra room for windows programs you'll install. then make a FAT32 partition for file sharing between the two. Linux will write into an ntfs partition, but it has been known to mess with the journaling, and Windows won't write into an ext 4 system. so you'd have to maintain two copies of any document and such you want to use in both and update them accordingly. However using wine, you can use MOST windows programs like OFFICE suite and such from the actual windows directory.

---

### Post by Spyderkid on 2011-12-03
Using a side-by-side partion install is usually more stable

---

