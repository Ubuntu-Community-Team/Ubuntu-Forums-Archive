---
title: "AV to scan windows?"
date: 2011-06-03
forum: General Help
---

### Post by TechnicalMechanic on 2011-06-03
Just a quick question, is there an AV i can use to scan my windows partition to find any  bugs/backdoors or viruses?

I know there is a backdoor somewhere, and comodo isnt picking it up so i am refusing to boot from my windows 7 right now. My password information keeps getting changed and websites and emails are alerting me that someone has access to them and is trying to promote spam.


Halp, thanks.

---

### Post by lmarmisa on 2011-06-03
Try to use Clamtk and ClamAV:

[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

Other interesting tool is AVG Rescue CD:

[http://free.avg.com/us-en/226162](http://free.avg.com/us-en/226162)

---

### Post by WorMzy on 2011-06-03
+1 for clamav. Clamtk is an optional front-end for it. If you're used to command-line applications, you don't need to bother installing it.

---

### Post by TechnicalMechanic on 2011-06-03
Clamtk installed, but not sure how to select the windows partition if ubuntu and 7 are sharing the same hdd?

---

### Post by lmarmisa on 2011-06-03
> **TechnicalMechanic said:**
> Clamtk installed, but not sure how to select the windows partition if ubuntu and 7 are sharing the same hdd?

Open a terminal and type this command:

```

sudo fdisk -l

```

Post the results in this thead.

---

### Post by linuxinstalledfromhdd on 2011-06-03
bitdefender

about 1/4 the way down the page. .

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by sixcorners on 2011-06-03
[http://connect.microsoft.com/systemsweeper](http://connect.microsoft.com/systemsweeper)

---

### Post by TechnicalMechanic on 2011-06-03
```

pentest@ubuntu:~$ sudo fdisk -l
[sudo] password for pentest: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eb80b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38914   312568832    7  HPFS/NTFS

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc4dcb34c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          13       91202   732469248    7  HPFS/NTFS

Disk /dev/sde: 7742 MB, 7742685184 bytes
84 heads, 38 sectors/track, 4737 cylinders
Units = cylinders of 3192 * 512 = 1634304 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               3        4738     7557120    b  W95 FAT32
pentest@ubuntu:~$ mount /dev/sdb1
mount: according to mtab, /dev/sdb1 is already mounted on /host
mount failed
pentest@ubuntu:~$ 


```

the 750.2 (/dev/sdb) is the hdd im needing to scan. /dev/sdb1 is windows 7 partition i believe.

---

### Post by lmarmisa on 2011-06-03
You could scan all the NTFS partitions: /dev/sda1 and /dev/sdb1.

Are you running Wubi or Ubuntu Live USB?

---

### Post by TechnicalMechanic on 2011-06-03
> **lmarmisa said:**
> You could scan all the NTFS partitions: /dev/sda1 and /dev/sdb1.

Are you running Wubi or Ubuntu Live USB?

Im on a full installation on the 750gb hdd. The partition is split, ubuntu 11.04 has about 21gb and 7 has the rest

---

### Post by lmarmisa on 2011-06-03
> **TechnicalMechanic said:**
> Im on a full installation on the 750gb hdd. The partition is split, ubuntu 11.04 has about 21gb and 7 has the rest

The command fdisk shows only one partition on your 750GB hdd:

```

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc4dcb34c

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Blue"]/dev/sdb1   *          13       91202   732469248    7  HPFS/NTFS[/COLOR]


```

---

### Post by TechnicalMechanic on 2011-06-03
Found the files in /host but still cant scan them for some reason. Clamav, clamtk, and bitdefender crash/timeout. Thinking it has something to do with permissions. going to try to run as sudo

---

### Post by lmarmisa on 2011-06-03
You are running Ubuntu Wubi. This is the reason because you have only one partition (/dev/sdb1).

Try this command if you wish to scan the disk:

```

sudo clamscan -r /host/

```

If you wish to remove the infected files, type this another command (the infected files will be removed, so be careful with this option):

```

sudo clamscan -r --remove=yes /host/

```

If you wish more information type the command:

```

man clamscan

```

---

### Post by TechnicalMechanic on 2011-06-03
Oh wait, wubi is when you install through windows correct?

forgot... but i ran clamtk as sudo under the prompt and its now scanning /host

---

### Post by lmarmisa on 2011-06-03
> **TechnicalMechanic said:**
> Oh wait, wubi is when you install through windows correct?


Yes, you are right.

---

### Post by TechnicalMechanic on 2011-06-04
Yay! 5 Viruses deleted. They happened to be located in some files i had saved for my wife from her old hard drive.... figures!

Sorry to bother you guys with this again, but is it safe to go back? Ive heard of programs that can scan processes and find which are malicious but unsure of the name at the moment...


Besides, im having so much fun on linux!

---

