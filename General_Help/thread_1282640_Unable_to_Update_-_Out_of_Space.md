---
title: "Unable to Update - Out of Space"
date: 2009-10-04
forum: General Help
---

### Post by fbergski on 2009-10-04
Noob here with my first install of Ubuntu on a Compaq Presario I received from my father-in-law.  Everything went well I installed with a dual boot system (Windows XP).  

Update manager popped up today with updates but when I say update it says that it cannot install because I'm out of disk space.  From looking at the file system folder I only have 120mb left.  Updates needs a total of 475mb to update so I'm assuming that the file system folder needs to get bigger somehow.

I don't really need the Windows partition, Ubuntu is faster on this computer and I've already configured my wireless device to enjoy streaming music (that's all I use the computer for).  

I guess the question is can I delete the Windows partition to give Ubuntu more room or is there something else I can do?

Thanks,

Philip

---

### Post by sports fan Matt on 2009-10-04
Whats the total space on the HD?..Its your choice if you want to delete the windows partition.

---

### Post by snowpine on 2009-10-04
Reboot using an Ubuntu Live CD, then use the Gparted partition editor to shrink your Windows partition and expand your Ubuntu partition. 

I would recommend keeping the dual boot with Windows; it is handy to have every once in a while (for example I use mine for watching netflix and mlb.com).

---

### Post by Snatcher on 2009-10-04
When you installed ubuntu  should have resized the disk. Giving ubuntu more room, ubuntu needs 4 gb of space. I would re-format the drive and install ubuntu without it being dual boot.

---

### Post by drs305 on 2009-10-04
fbergski,

Welcome to Ubuntu and the Ubuntu forums.

Did you select "side by side" with Windows? If you didn't slide the partitioning bar, you probably ended up with a / partition of less than 2.5GB. It's a bug in the installation process (Step 4, Partitioning).

Look at the results of this command:
```

df -h

```

If it shows / nearly full and 2.5GB or less you can either reinstall and modify things in Step 4, or resize the / partition and take space from another partition.

I've written guides on how to do both:

If you have a 2.5 GB partition and want to reinstall:
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")

If you have a 2.5 GB partition and want to resize the partition:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by fbergski on 2009-10-04
Thanks for all the help.  After reading the last post I've decided just to reinstall Ubuntu.  First install went was pretty easy so the second time around should be even easier.  I'm going to make the Ubuntu partition at least 10GB.

Philip

---

### Post by fbergski on 2009-10-05
New install is done and works fine :) successfully downloaded updates.  

I chose to use the whole drive to install Jaunty, don't really care that XP isn't on it.  Have three other computers with XP if I need it.  Now the fun begins :).  

Thanks to all for the help.

Philip

---

