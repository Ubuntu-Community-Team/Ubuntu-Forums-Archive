---
title: "GParted filled up a partition after resizing"
date: 2009-07-04
forum: General Help
---

### Post by Yes on 2009-07-04
I just booted the GParted live CD to shrink one partition and grow another.  The one shrunk to the right size and the other one seems to have grown to the right size, but according to GParted it's still 95% full, just like it was before I added 110 GB to it.  Does anyone have any idea what happened?

Thanks!

---

### Post by merlinus on 2009-07-04
Try restarting.

---

### Post by Yes on 2009-07-04
I have.  I rebooted and ran fsck from an Ubuntu live CD (which also reported it being 95% full), didn't get any errors, rebooted again and it still says it's 95% full.

---

### Post by merlinus on 2009-07-04
Can you post a screenshot of gparted?  Did you use it from ubuntu, the one on the ubuntu cd or its own live disk?

Also, results of

```
df -h
```

might be useful, as well as
```

sudo fdisk -l
```

---

### Post by Yes on 2009-07-04
df -h:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda9              57G   54G  521M 100% /
none                 1013M     0 1013M   0% /dev/shm
/dev/sda10            2.1G   84M  2.0G   5% /boot
/dev/sda8              79G   30G   48G  39% /home/alex/data
```

fdisk -l:

```
Disk /dev/sda: 320.0 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x81018101

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       38913   281852392+   5  Extended
/dev/sda5            3825        4250     3421813+  83  Linux
/dev/sda6            4251        5162     7325608+  83  Linux
/dev/sda7            5163        5466     2441848+  82  Linux swap / Solaris
/dev/sda8            5467       15887    83706651   83  Linux
/dev/sda9           15888       38635   182723278+  83  Linux
/dev/sda10          38636       38913     2233003+  83  Linux
```

I ran GParted from the GParted live CD, not the Ubuntu Live CD.  I've attached a screenshot of GParted.

The problem partition is /dev/sda9

---

### Post by merlinus on 2009-07-04
What do you have in / that is using up almost 172G?  And what is sda5 and sda6?

I wonder if in resizing data was copied over from another partition?

```
du
```

will show just about everything.

---

### Post by Yes on 2009-07-04
Like I said, nothing.  It used to be about 60 GB and 95% full, so I took some space from my old Ubuntu install (the partition in question is my Arch install) and grew it up to about 175 GB.  But after I added all that space, it still says it's 95% full.

sda5 and sda6 are the /boot and / partitions for my Ubuntu install.

I thought that might be the case, but I didn't have 172 GB of data on the entire disk before.  And if it did copy it over, where is it now?  I've looked and I cant find it on sda9

---

### Post by merlinus on 2009-07-04
sda5 and sda6 have no mountpoints, according to gparted.  sda9 is mounted as /.

---

### Post by Yes on 2009-07-04
I know, I'm running Arch Linux at the moment.  sda5 and sda6 aren't mounted, sda9 is the root partition for my Arch install which is why it's mounted as /

---

### Post by merlinus on 2009-07-04
```
sudo du -mx --max-depth=1 / | sort -g
```

will show the usage of everything within /.  Maybe you can find a culprit!

---

### Post by Yes on 2009-07-04
Dunno, does this help?

```
0	/dev
0	/proc
0	/sys
1	/.kde
1	/.qt
1	/boot
1	/lost+found
1	/mnt
1	/srv
1	/tmp
5	/bin
7	/root
13	/sbin
54	/media
73	/etc
232	/lib
2830	/opt
5535	/usr
10506	/var
35647	/home
54898	/
```

---

### Post by merlinus on 2009-07-04
```
du -h
```might give a better idea, but still, I cannot see how so many Gs are being used!  Weird...

You don't by chance have an external hdd plugged in?

---

### Post by Yes on 2009-07-04
Nope, no external hard drive.

du -h gives a ton of results, is there any way to list them by size order?

---

### Post by merlinus on 2009-07-04
cd to /

```
du -sk .[A-z]* *|[sort]("http://en.wikipedia.org/wiki/Sort_%28Unix%29") -n
```

---

### Post by drs305 on 2009-07-04
If you feel the drive is reporting the correct size but there is something actually filling up the drive, the "DiskSpace" link in my signature line takes you to a guide that discusses some of the things that fill up a partition, how to find them and how to correct them.

The most common things are undeleted trash, backups mistakenly saved to the system partition instead of an external device, and large log files. The guide covers all these and others.


If the device isn't reporting the correct *total* size, the resize2fs command can help. Normally this command is only needed when a smaller partition is cloned into a larger one. Linux sometimes won't recognize the new size until "resize2fs" is run. Read about it at "man resize2fs".

---

### Post by Yes on 2009-07-04
```
0	openoffice-base-3.0.0-3-i686.pkg.tar.gz.part.1
0	proc
0	python-2.6-2-i686.pkg.tar.gz.part.1
0	sys
0	xcb-proto-1.2-1-i686.pkg.tar.gz.part.1
12	mnt
16	lost+found
24	.qt
64	dev
84	srv
88	tmp
276	.kde
4240	bin
6652	root
13184	sbin
16364	boot
54276	media
74128	etc
237080	lib
2897488	opt
5667760	usr
10758152	var
67479056	home
```

And thanks for all the help :)

@drs - I have no reason to think the drive is reporting the incorrect size.  But since right after enlarging the partition it was still saying it was 95% full, I don't think the issue is a large trash or backups accidentally on the main drive.  The device is reporting the correct total size, of about 175 GB.

---

### Post by merlinus on 2009-07-04
I believe these numbers are kilobytes, so you will have to do some converting to get them in M and G.

Also, be sure to check the guide drs305 mentions.

---

### Post by Yes on 2009-07-04
Are you sure they're kilobytes?  That would mean that my home directory is taking up 64 GB, thats way more than it should be taking up.

I'll check that link now, and try and figure out what's taking up so much space.

e:  It's counting the 30 GB of another partition that's mounted in a folder in my home folder, so that all looks normal.

e2: I ran resize2fs /dev/sda9 like suggested in the link and everything is showing up normally now.  Thanks so much :)

---

