---
title: "Transfering data between partitions and unpartitioning hard drive?"
date: 2011-04-10
forum: General Help
---

### Post by nostromo72 on 2011-04-10
So this is a two part question. 
My laptop came preinstalled with windows 7, I wanted ubuntu but needed windows to update my zune so I have both operating systems on my laptop. I only used windows for my zune, that was its sole purpose, now my zune is broken and I no longer need windows at all. 

First, I downloaded about 20gb of music off of my zune and onto my windows partition, is there any way to transfer files like these from one partition to another? I don't know if that makes sense. 

Second, can I unpartition my hard drive so it is purely ubuntu ** without losing all my ubuntu files and stuff **? If that wasn't clear, I want my laptop to just have ubuntu, I want the 40-some gb that I dedicated to windows back for ubuntu, and I don't want to lose all my files, settings, etc. that I already have on my ubuntu partition. Can this be done?

Thanks

---

### Post by ~Plue on 2011-04-10
> **nostromo72 said:**
> First, I downloaded about 20gb of music off of my zune and onto my windows partition, is there any way to transfer files like these from one partition to another? I don't know if that makes sense.
 
sure. just mount>open the windows partition from the places menu > cut/paste the files into your home folder

> **nostromo72 said:**
> 
Second, can I unpartition my hard drive so it is purely ubuntu ** without losing all my ubuntu files and stuff **? If that wasn't clear, I want my laptop to just have ubuntu, I want the 40-some gb that I dedicated to windows back for ubuntu, and I don't want to lose all my files, settings, etc. that I already have on my ubuntu partition. Can this be done?

it is possible to resize the partitions using gpaterted, but you'll need to do it from a live cd since mounted filesystems cannot be modified

(its good practice to backup important data before moving/resizing partitions, since a power failure or something of the sort during the process could damage it)

---

### Post by seawolf167 on 2011-04-10
Transfer files:

Boot into Ubuntu, look for Places -> 40GB Filesystem (that was the naming convention in 10.04), if you don't find something similar, it should be listed in /mediaOnce you open the filesystem (you'll need to enter your password) simply browse to the location of your music and copy it over to you Ubuntu install (say ~/Music folder)

Remove windows:

You can do some work while booted in Ubuntu - fire up GParted (System -> Administration -> GParted), there you can delete (unallocate) or re-format your Windows partition to ext.

After that you'll need to boot off a LiveCD, then re-fire up GParted and depending on how your partitioning scheme is layed out (i.e. separate partitions for /, /home, /boot, etc.) you can resize the partitions into your now free (formally-Windows) space.

---

