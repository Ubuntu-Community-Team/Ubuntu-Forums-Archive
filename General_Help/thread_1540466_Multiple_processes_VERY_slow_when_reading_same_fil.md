---
title: "Multiple processes VERY slow when reading same file"
date: 2010-07-27
forum: General Help
---

### Post by lazyfirecloud on 2010-07-27
I know this may not be specific to ubuntu but I was wondering if anyone had knowledge in this area.

After running out of space on my hard drive, I've decided to do a clean install. Unfortunately, I've done several changes (this is on the same machine)

* old drive had one partition with both OS and data, new drive has two partitions
* old drive was ext3, new drive was ext4
* old drive ran Jaunty, new drive has Lucid

Ever since I did this upgrade, running multiple processes writing files using Magick++, it takes forever. It takes much longer than running them sequentially in fact, even though I have 8 logical cores. This was not the case previously (same code). Right now, running them sequentially works fine. The new hard drive is technically faster than the old.

I was just wondering if there was something dumb I didn't know that could be causing this. Or if anyone had any clues on what could be causing this: hard drive specs, ext3 vs ext4, ubuntu upgrade, partitioning, new ImageMagick version (not sure if the default package changed between Jaunty and Lucid).

Otherwise, I'll just have to try to use my old hard drive again but it would be a shame to roll back (and it's still out of space).

Any help is appreciated! Thanks is advance =)

Below is my fstab if it's of any help. 

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=ce9c680b-cabf-41b3-96ff-ea8353891687 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=afa4c70b-0189-4ca0-88fe-35e88993e274 none            swap    sw              0       0

#data
UUID=c87e0f75-09d6-4894-9bc2-922fb2cd2205 /zdata          ext4    relatime,errors=remount-ro,defaults,rw,user,noexec 0       0

# windows share drives
//dontpanic/share                /mnt/dontpanic/share     cifs   credentials=/root/.smbcredentials.dontpanic1,uid=1000,gid=1000,file_mode=0600,dir_mode=0700 0       0

```

---

### Post by robsoles on 2010-07-28
Hi, it's logical to me - mind you I haven't tried the software you are talking about and I only go from years of both making my own software to do stuff and simultaneously not bothering and just considering what the makers of the software I was using to do stuff had to be doing to get it done.

Magick++ was utilising the 8 threads/cores better before - now there is a clash in the way they are addressing the 'multithreadingness' capabilities of the CPU/MB/OS and 'dropping the ball' where it was previously (even if only 'flukily') quite ""clever"".

I think that I have established that I don't know for sure but it's likely that I am probably right - as a cheap 'workaround' you could just use it sequentially, sorry.

---

### Post by lazyfirecloud on 2010-07-28
You may be right. It looks like the newer versions of ImageMagick support multi-threading. Maybe the previous version didn't so I could run 8 processes on my 8 cores. The sad part is I don't think it runs faster my 8 cores. If I run 2 simultaneously, it slows down to a crawl and I end up having to just kill one of them. I used to run 5-6 with no problems. Oh well. Thanks for the help.

---

### Post by lazyfirecloud on 2011-01-06
By the way, for anyone who has the same problem, setting environment variable OMP_NUM_THREADS=1 works like a charm. Forces it to be single threaded again.

---

