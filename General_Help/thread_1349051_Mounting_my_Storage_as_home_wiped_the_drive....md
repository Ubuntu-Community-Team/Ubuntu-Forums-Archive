---
title: "Mounting my Storage as /home wiped the drive..."
date: 2009-12-07
forum: General Help
---

### Post by beastrace91 on 2009-12-07
Hey All,

So I just did a fresh install of Ubuntu 9.10 on my laptop (I dislike upgrading). Besides the point - up until now I'd had a storage partition that I used to store data on and this time around I choose to mount my old storage partition to be used as /home - during the manual partition process, when I did so I was VERY careful not to check the "format" box for /home. However when I booted into Karmic for the first time I see all my files are gone. There wasn't anything on the storage partition I cannot replace however I am wondering why this happened exactly? If someone could shed some light on it I would be much appreciated.

Regards,
~Jeff

---

### Post by jbrown96 on 2009-12-07
The only reason that I could think of is that you changed the file system type. Perhaps, it would let you uncheck the format option, but the file system choice was incorrect, and it fromatted it without warning you.

Too bad you lost your files.

---

### Post by beastrace91 on 2009-12-07
Nope I left it as ext3 - and it was very CLEARLY unchecked. Am I correct in assuming it should have just added the directories it needs to be /home and the rest should have been left as is? Is this an error in the partitioner or am I not understanding something correctly?

~Jeff

---

### Post by lloyd_b on 2009-12-07
> **beastrace91 said:**
> Hey All,

So I just did a fresh install of Ubuntu 9.10 on my laptop (I dislike upgrading). Besides the point - up until now I'd had a storage partition that I used to store data on and this time around I choose to mount my old storage partition to be used as /home - during the manual partition process, when I did so I was VERY careful not to check the "format" box for /home. However when I booted into Karmic for the first time I see all my files are gone. There wasn't anything on the storage partition I cannot replace however I am wondering why this happened exactly? If someone could shed some light on it I would be much appreciated.

Regards,
~Jeff

Could you post the output of the terminal command "df"?  Just to make sure that your "storage" partition is in fact mounted at "/home"?

If for some reason it isn't being mounted, then /home *would* be empty...

Lloyd B.

---

### Post by beastrace91 on 2009-12-07
I'll post the output of that command when I get back home - but I checked under every rock (fdisk -l), nook (gparted), and cranny (poking around my root directory) - and could not find it. Plus my /home is listed as /dev/sda5 (which is where my old storage partition was).

~Jeff

---

### Post by tgalati4 on 2009-12-07
It sounds like your /home partition didn't get mounted.  Errors should show up in dmesg if there is a problem.  Post the output of:

sudo fdisk -l

---

### Post by beastrace91 on 2009-12-08
Oh its there & its mounted - just like I said its wiped clean.

I think I'm going to set up the same setup again in a VM and see if I can reproduce the issue.

I'll also post the output of the above two suggested commands when I get home just to prove I'm not crazy... ;)

Cheers,
~Jeff

---

### Post by beastrace91 on 2009-12-08
```
jeff@sager-lintop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7             19995348   3124856  15854784  17% /
udev                   2027876       332   2027544   1% /dev
none                   2027876       332   2027544   1% /dev/shm
none                   2027876       108   2027768   1% /var/run
none                   2027876         0   2027876   0% /var/lock
none                   2027876         0   2027876   0% /lib/init/rw
/dev/sda1                93307     37070     51420  42% /boot
/dev/sda5             89010852  55437472  29051892  66% /home
/dev/sda6            129693584  85865920  43827664  67% /mnt/Steam
/dev/sda3             67961852  20116132  47845720  30% /mnt/Windows
/dev/sdb1            488383484 445186700  43196784  92% /media/500GB Ex
jeff@sager-lintop:~$ sudo fdisk -l
[sudo] password for jeff: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003e829

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  83  Linux
/dev/sda2              13         510     4000185   82  Linux swap / Solaris
/dev/sda3   *         511        8971    67961856    7  HPFS/NTFS
/dev/sda4            8972       38913   240509115    5  Extended
/dev/sda5            8973       20230    90429885   83  Linux
/dev/sda6           20231       36384   129756973+   b  W95 FAT32
/dev/sda7           36385       38913    20314161   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8d9b254

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488383488    7  HPFS/NTFS

```

Its there and mounted just like I said :-/

I'll have to try and see if I can reproduce the error or if it was a one time thing...

Regards,
~Jeff

---

### Post by tgalati4 on 2009-12-08
Perhaps sda3 (ntfs) tripped up the extended partition (sda4) which forced a mkfs on sda5.

---

### Post by lloyd_b on 2009-12-08
> **beastrace91 said:**
> [code]jeff@sager-lintop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7             19995348   3124856  15854784  17% /
udev                   2027876       332   2027544   1% /dev
none                   2027876       332   2027544   1% /dev/shm
none                   2027876       108   2027768   1% /var/run
none                   2027876         0   2027876   0% /var/lock
none                   2027876         0   2027876   0% /lib/init/rw
/dev/sda1                93307     37070     51420  42% /boot
/dev/sda5             89010852  55437472  29051892  66% /home
/dev/sda6            129693584  85865920  43827664  67% /mnt/Steam
/dev/sda3             67961852  20116132  47845720  30% /mnt/Windows
/dev/sdb1            488383484 445186700  43196784  92% /media/500GB Ex

Its there and mounted just like I said :-/

I'll have to try and see if I can reproduce the error or if it was a one time thing...

Regards,
~Jeff

Have you already restored everything to that partition?  I'm assuming that's what using the 55GB of space on that drive.

If not, do a "ls /home" and see what's there.

Lloyd B.

---

### Post by beastrace91 on 2009-12-08
No I did not yet restore my files to the drive, so maybe they are still there (I hadn't noticed that the space was still taken up) when I run **ls -a** on my /home it does not list any of my old files. Suggestions on how I might find them if they are stilll there taking up space?

~Jeff

---

### Post by lloyd_b on 2009-12-08
> **beastrace91 said:**
> No I did not yet restore my files to the drive, so maybe they are still there (I hadn't noticed that the space was still taken up) when I run **ls -a** on my /home it does not list any of my old files. Suggestions on how I might find them if they are stilll there taking up space?

~Jeff

Try a "find /home -name "somefile" -print", where "somefile" is the name of a file you know was on that data partition.

Lloyd B.

---

### Post by beastrace91 on 2009-12-08
Ahhh I feel like such a fool! I was looking in ~/ not /home - naturally all my files where in the top most level of /home :oops:

Thanks for the input all :)

Regards,
~Jeff

---

