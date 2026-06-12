---
title: "Help with transfering current ubuntu installation to a new SSD"
date: 2010-01-18
forum: General Help
---

### Post by axima on 2010-01-18
Here is the situation. I bought a 30 GB SSD and I need to install Ubuntu on it. I currently have a 1500 GB harddrive, on it my current 60gb ubuntu partition and the rest is Windows 7. 

Out of the 60 GB for ubuntu I have used 9 GB, so I want to transfer that 9GB to the SSD to preserve all my settings. Then I want to format the original 60GB to something else, probably NTFS since both linux and windows can read it. 

What are the steps to do this? This is possible, correct?  

I tried sbackup but that creates a back up on my current drive, not what I intended. If there is a gui program that will work that would be great, if not I'll still give whatever suggested a shot.

axima

---

### Post by blackened on 2010-01-18
```
sudo dd if=/dev/sda1 of=/dev/sdb1
```

Granted, I don't think this will work unless you first shrink your original root partition (the one on the harddrive) to less than or equal to 30Gb.

After that you'll still need to fix grub. Look around on google, I'm sure there are plenty of howtos to get this done.

---

### Post by argosreality on 2010-01-18
You could use a gparted [Live CD]("http://gparted.sourceforge.net/livecd.php")to shrink the partitions and then use dd to clone the drive to the new SSD. However, I dont think dd will automatically do sector alignment correctly for what SSDs require for good performance (and of course I cant find the article about it from anandtech).

---

### Post by warfacegod on 2010-01-19
This is a guide on how to create a compressed file of your entire system or whatever parts of it you choose. After doing that you can then take that file and unpack it in a fresh install of Linux and your old system will be reinstalled. I've used this several times with much success.

[http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

---

### Post by axima on 2010-01-20
I guess I will just do a reinstall, it was foolish of me to spend the time customizing my ubuntu just the way i like it. and in april i have to do another reinstall for the new 10.04, things are moving quickly, great for ubuntu.

---

### Post by warfacegod on 2010-01-20
> **axima said:**
> I guess I will just do a reinstall, it was foolish of me to spend the time customizing my ubuntu just the way i like it. and in april i have to do another reinstall for the new 10.04, things are moving quickly, great for ubuntu.

If you follow the link I posted, you won't have to lose your setup.

---

### Post by bpalone on 2010-01-20
Use GParted Live CD and shrink your current Ubuntu partition.  Then copy that partition to the new drive.  The worst you will have to do is re-install grub.

---

### Post by cariboo on 2010-01-20
Have a look at partimage, it is in the repositories. It will make an image of your partition, ignoring the empty space.

---

### Post by axima on 2010-01-20
i searched for partimage in synaptic but i get a result that says it is just documention is that the correct file?

---

### Post by warfacegod on 2010-01-20
> **axima said:**
> i searched for partimage in synaptic but i get a result that says it is just documention is that the correct file?

No, documentation is just that, documents. Basically a diary of the app. If you type "partimage" into your search bar you should see three entries.

partimage-server
partimage
partimage-doc

You want the one in the middle with no *-something* after its name.

---

### Post by axima on 2010-01-20
> **warfacegod said:**
> No, documentation is just that, documents. Basically a diary of the app. If you type "partimage" into your search bar you should see three entries.

partimage-server
partimage
partimage-doc

You want the one in the middle with no *-something* after its name.

i don't see that, only the last entry. i am running 64 bit 9.10, my OS can't be outdated can it?

---

### Post by warfacegod on 2010-01-20
> **axima said:**
> i don't see that, only the last entry. i am running 64 bit 9.10, my OS can't be outdated can it?

Not likely. Check Software Sources under the Ubuntu Software tab to see if you have multiverse enabled and the Other Software tab to see if ubuntu karmic *partner* is enabled. Let it reload the sources and then go to Update Manager and get all updates. After that, head over to Synaptic and under Edit, select Fix Broken Packages and then look for partimage again.

If it still only shows the documentation, the only thing I can think of is that it won't run on a 64 Bit OS. That would explain why it only shows the docs, because after all, anybody can read a text file regardless of architecture and hardware.

---

### Post by axima on 2010-01-20
I wasn't able to find it so I just went on with the resintall. ssd is pretty good, i hope 10.04 supports trim.

---

### Post by warfacegod on 2010-01-20
> **axima said:**
> I wasn't able to find it so I just went on with the resintall. ssd is pretty good, i hope 10.04 supports trim.

How is the performance compared to your old drive?

---

### Post by axima on 2010-01-21
good, boots faster, everything a bit snappier, well worth it i say. other than that not much difference so far, but i just firefox 99% of the time.

will 10.04 support trim?

---

### Post by warfacegod on 2010-01-21
After hunting around a bit, it looks like 9.10 supports it at the command line level (you'll have to do it your self periodically). At least that's what I gather so I would imagine 10.04 would have better support. I would post a new thread on it in the Community Cafe for a better answer than that.

---

### Post by hwttdz on 2010-01-21
Most of the "customizations" you speak of are in your ~ anyways.  So in the future a relatively easy way to do this is to get a fresh install and then pull your home in from another drive (made easier if you have a different partition for home and /).  I also keep a sort of script of all the commands I've run using sudo permissions (which is actually easier than it sounds), I just do "history|grep "sudo apt-get"" at the end of the day (for the first few days of using a machine) or something of the sort, and then put that in a text file keeping track of what I've put on there.  So after dropping in my old ~ and running my sudo script my machine is set up just as before.

---

