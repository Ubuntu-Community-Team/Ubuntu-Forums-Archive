---
title: "missing hard drive space"
date: 2010-05-02
forum: General Help
---

### Post by icd* on 2010-05-02
i've had a good look all over the internet but didn't find anything of much use to me. im running ubuntu 9.10 on a toshiba 80GB laptop. basically, looking on Disk Usage Analyser i'm told the total capacity is 70.3GB with 61.5GB used and 8.9GB available.
But after scanning the filesystem it tells me that "/" is using up 16.7GB, so where's the rest of my hard drive?

i also opened up the disk utility program which says there's 77GB unknown or unused mounted at /dev/sda1 which i assume is where the filesystem is. also there's 3.3GB extended which i also assume is swap so i'd love to know why it says "unknown or unused".

i'm looking to upgrade to 10.04 soon so i don't want to upgrade and then ask for help only to be told i need to format the hard drive or something or other. help would be appreciated. =] i don't know if you need any logs or results from certain commands, sorry about that.

---

### Post by MooPi on 2010-05-02
Open a terminal and 
```
sudo fdisk -l
```then try 
```
df -h
```paste results back here

---

### Post by icd* on 2010-05-02
joey@house-laptop:~$ sudo fdisk -l
[sudo] password for joey: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5542e38c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris
_____________________________________

joey@house-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   62G  5.3G  93% /
udev                  943M  164K  943M   1% /dev
none                  943M  8.5M  935M   1% /dev/shm
none                  943M  208K  943M   1% /var/run
none                  943M     0  943M   0% /var/lock
none                  943M     0  943M   0% /lib/init/rw

---

### Post by MooPi on 2010-05-02
From the results you posted the drive is nearly full and upon reading a little closer from you original post I can guess that your root portion is 16.7 gig and not the whole contents of your sda1 partition.I'm going to assume you have 2 gigs of ram as your swap partition is 3.3gigs. If you upgrade I suggest reducing your swap size as it's waisted space. One gig of swap should be sufficient with the exception in extreme situations. Do you have a large video or music collection that is consuming the hard drive ?

---

### Post by icd* on 2010-05-02
well, i did have a video and music collection but as i was constantly being told there was little space left i ended up deleting the whole lot. and yes root is only using 16.7GB. i just don't know how to get that other 50oddGB back. there's nothing in the wastebasket, my home folder only contains 9.3GB out of the 16.7GB total that the disk usage analyser tells me i have.

edit: is it a case of me doing bad formatting/partitioning when i installed ubuntu way back or what? i am tempted to download ubuntu 10.04 and just wipe the hard drive but obviously upgrading would be simpler and easier. also, i just ran a self-test on the hard drive and it says the disk is completely healthy, no errors or bad sectors.

---

### Post by MooPi on 2010-05-02
If you have the capacity to save your remaining data, then a fresh install would be an option. Can't comment on your partitioning from past but have seen similar posts on the same subject. Sometimes the simplest is not the best. I prefer fresh installs but I save all my data to either external drives or separate partitions.

---

### Post by icd* on 2010-05-02
i guess i've been beaten again. ill backup the stuff i need and do a clean install. thanks for the help.

---

### Post by srs5694 on 2010-05-02
I don't see why you think that root (/) is only 17.6GB. From your df -h output:

```

/dev/sda1              71G   62G  5.3G  93% /

```

This clearly indicates that root (/) is 71GB in size, with 62GB used and 5.3GB free.

You can learn where this space is being used by using du and sorting the result:

```

sudo du -s /* | sort -n

```

The result will be a list of directories, with associated space consumed, sorted by the latter. You can repeat this process for particular directories, as in:

```

sudo du -s /home/* | sort -n

```

This example sorts the subdirectories of /home according to how much space each consumes. Note that these commands can take several minutes to execute, so be patient.

If you do decide to wipe everything and reinstall, I recommend you create a separate /home partition. Make your root (/) partition 5-20GB, depending on how much software you intend to install, and give the rest to /home. This will simplify future upgrades/reinstallations, since you'll be able to wipe your main install without touching your user files.

---

### Post by krismatth3 on 2010-05-02
Again, as I posted in response to your last post on this subject; you are misunderstanding the output of graphical disk analyzer. That is the entire problem.

---

### Post by dtmbmw325i on 2010-05-03
Since you were deleting things and if you didn't reformat and install it may be worth looking at this thread.  I just solved my issue with it.  Basically it came down to not emptying the root (as in user) trash bin.  See if this helps it did for me.

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

