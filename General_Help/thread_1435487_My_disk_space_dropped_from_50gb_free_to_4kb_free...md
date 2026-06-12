---
title: "My disk space dropped from 50gb free to 4kb free..."
date: 2010-03-21
forum: General Help
---

### Post by wqawasmi on 2010-03-21
Ubuntu 9.10 Karmic
I downloaded Folding@Home today, used it for a bit. 


Suddenly I get a message saying I only have 1gb of disk space left.

I panic and kill Folding@Home. 

Then I get another message saying I have 8kb disk space left.

Then another saying I have 4kb disk space left.

I'm not sure what just happened but if I could get my disk space back the would be great.

Thanks in advance,

-Will Qawasmi

---

### Post by llamabr on 2010-03-21
weird.  I don't know anything about this problem, but probably it's filling up your /tmp file with huge images, or else filling up its hidden directory with backups and config and things.

check /tmp

and look for something like ~/.folding/

---

### Post by Usabent on 2010-03-21
Looks like a new bug. You should report it. To get it back can you give us the information on your drive? Just go to command and use

```
Sudo Fdisk -l
```

---

### Post by wqawasmi on 2010-03-21
> **llamabr said:**
> weird.  I don't know anything about this problem, but probably it's filling up your /tmp file with huge images, or else filling up its hidden directory with backups and config and things.

check /tmp

and look for something like ~/.folding/

Checked it, only 28kbs in /tmp

---

### Post by wqawasmi on 2010-03-21
> **Usabent said:**
> Looks like a new bug. You should report it. To get it back can you give us the information on your drive? Just go to command and use

```
Sudo Fdisk -l
```
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2df12df0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       96105   771855360    7  HPFS/NTFS
/dev/sda3          108853      121601   102401024   83  Linux
/dev/sda4           96106      108852   102390277+   5  Extended
/dev/sda5           96106       96168      506016   83  Linux
/dev/sda6           96169      106417    82325061   83  Linux
/dev/sda7          106418      108852    19559106   82  Linux swap / Solaris

Partition table entries are not in disk order

```

/dev/sda3 is my Ubuntu partition. 

The rest is Arch and Windows.

---

### Post by 2hot6ft2 on 2010-03-21
If the warning is coming from the Disk Usage Analyzer, it only shows how the files are distributed within the file system and not the space on your partition.

Open a terminal
Applications > Accessories > Terminal
and run
```
df -h
```
Your results will be something like
So in this it's more representative of the actual use of the partitions space.
```
Filesystem            Size  Used Avail Use% Mounted on
**[COLOR="Blue"]/dev/sda8              40G  9.9G   28G  27% /[/COLOR]**
udev                  1.4G  328K  1.4G   1% /dev
none                  1.4G  420K  1.4G   1% /dev/shm
none                  1.4G  208K  1.4G   1% /var/run
none                  1.4G     0  1.4G   0% /var/lock
none                  1.4G     0  1.4G   0% /lib/init/rw
```

Meaning that roughly 27% of the partition is being used by the file system.

I already asked the same question and it was cleared up in this thread.
[http://ubuntuforums.org/showthread.php?t=1410114](http://ubuntuforums.org/showthread.php?t=1410114)

---

### Post by drs305 on 2010-03-21
If further investigation is required and it isn't a bug, here is a post that provides a guide to searching out the problem and possibly correcting it:

[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by wqawasmi on 2010-03-22
> **2hot6ft2 said:**
> If the warning is coming from the Disk Usage Analyzer, it only shows how the files are distributed within the file system and not the space on your partition.

Open a terminal
Applications > Accessories > Terminal
and run
```
df -h
```
Your results will be something like
So in this it's more representative of the actual use of the partitions space.
```
Filesystem            Size  Used Avail Use% Mounted on
**[COLOR="Blue"]/dev/sda8              40G  9.9G   28G  27% /[/COLOR]**
udev                  1.4G  328K  1.4G   1% /dev
none                  1.4G  420K  1.4G   1% /dev/shm
none                  1.4G  208K  1.4G   1% /var/run
none                  1.4G     0  1.4G   0% /var/lock
none                  1.4G     0  1.4G   0% /lib/init/rw
```

Meaning that roughly 27% of the partition is being used by the file system.

I already asked the same question and it was cleared up in this thread.
[http://ubuntuforums.org/showthread.php?t=1410114](http://ubuntuforums.org/showthread.php?t=1410114)

Thank You very much. 

It seems that after a couple of reboot's it finally stopped giving me the error, and Conky displayed my actual disk space. 

Another Problem solved by the Linux community!

---

