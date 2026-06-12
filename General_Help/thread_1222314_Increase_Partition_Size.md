---
title: "Increase Partition Size"
date: 2009-07-24
forum: General Help
---

### Post by bearsomg on 2009-07-24
I installed Ubuntu 9.04 on a separate hard drive on my computer from Windows on another hard drive. When I installed it I accidentally set the installation size to 5gb, but my hard drive is 18gb. I have run out of space, and I would like to know how to increase the size of that partition. I heard of GParted, but in that case, how can I burn ISO files to a CD from Ubuntu? I would really like to get this working.:confused:

---

### Post by philcamlin on 2009-07-24
boot intoyour ubuntu cd 

select live cd 

go to terminal > sudo apt-get install gparted

then type sudo gparted

then resize your partition and reboot !

---

### Post by realzippy on 2009-07-24
you can start your CD as liveCD and install gparted,if you have internet:then resize..

---

### Post by michy99 on 2009-07-24
Here's a nice how-to on increasing your Ubuntu partition:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by bearsomg on 2009-07-25
Well, one problem is I have only a CD burner, and the ubuntu ISO apparantly was too large to be burnt to the CD (ImgBurn, only about 5mb free space.) I installed Ubuntu by mounting it in a program called MagicDisc in Windows, and doing the windows istall for a dual-boot. I did find a stand-alone copy of gparted from their website, a separate live CD and burnt that one. I started that, and found that there was a lot of unallocated space so I resized the ubuntu partition and it lost all my files and wouldn't boot:( (good thing I didn't do anything major on it yet.) So now I'm doing a fresh install. Thanks for the help.:)

---

### Post by bearsomg on 2009-07-25
OK, now i'm confused. When I do a 5gb install, I don't get the full 18gb in the partition. But when I do the 18gb install, the installer completely fills up the entire hard drive. Can't I just do a regular install alongside windows where it only uses 5gb as the install location, but lets me use the entire hard drive to save my files?:confused::confused::confused::confused::confused::confused:

---

### Post by merlinus on 2009-07-25
Linux uses partitions for everything, so if you choose use entire hdd everything will be gone.

If you are wanting to dual-boot with windows, be sure to defrag several times first.  If using vista, use its disk management tool to shrink its partition.

Then you can choose a side-by-side installation for ubuntu.

---

### Post by bearsomg on 2009-07-25
> **merlinus said:**
> Linux uses partitions for everything, so if you choose use entire hdd everything will be gone.

If you are wanting to dual-boot with windows, be sure to defrag several times first.  If using vista, use its disk management tool to shrink its partition.

Then you can choose a side-by-side installation for ubuntu.
I am actually doing a triple boot with XP, and Windows 7, each on a separate hard drive. When I did the full install to the Ubuntu hard drive (all 18gb) Windows 7 said that it was full, but it wasn't because that space was saved for use by ubuntu only.

---

### Post by michy99 on 2009-07-25
So to make it clear to everyone, you are doing an install thorough Windows using Wubi. This is a different situation from a normal install from disk. Windows sets up a file which is used for your Ubuntu system and the size of the file is determined when you install. Windows will always see the file as the same size no matter what is in it. If you use the whole disk for the Ubuntu system, the file will fill the whole disk and it is "full" as far as windows is concerned. From Ubuntu, however you can see how much space is actually being used.

If you want, you can make the 5 gig setup from windows, and then make another partition on the rest of the disk for storing data.

---

### Post by bearsomg on 2009-07-25
Yea, I kind of figured out the size thing that Windows thinks it is full, but it partitioned for ubuntu. It is working fine now thatnks for all your help

---

