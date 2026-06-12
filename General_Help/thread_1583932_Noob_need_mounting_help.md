---
title: "Noob need mounting help"
date: 2010-09-28
forum: General Help
---

### Post by Jellax on 2010-09-28
Ok this is my plan.

I just installed Ubuntu 10.4 and need some help with mounting issues.
Remember, I am a total novice, I know nothing about the console, how it works etc.

I have a server with 2 internal sata drives and 2 external USB drives.
What I want to do is to make a setup of folders like this
movies
       - DVD
       - HD
       - Series
This set up of folders will be on all my drivers. I want to mount the content from USB1's HD folder to the top lever HD folder, and the same with DVD etc.
I want to do the same from USB2.

After that the folder structure should look like this:
movies
       - DVD-
             DVD1
             DVD2
       - HD-
             HD1
             HD2
And so on. Is this possible?
How can I do this?
Please note that I need really clear instructins, because I know absolutely nothing about hos anything is done in Linux. I need instructions that I more or less can copy and past and just add my labelnames of the drives.

Anyone that can help me with this will be considered a Linux god from now on :)

---

### Post by lrgmmc on 2010-09-28
you would use fstab to do that. what is the output from fdisk -l.
open terminal and past ```
fdisk -l
```

---

### Post by Jellax on 2010-09-28
Nothing happens, I just get back to the root

administrator@Server:~$

---

### Post by ddnev45 on 2010-09-28
You need to be root to use fdisk; in a terminal:

```
sudo fdisk -l
```

after you enter your password you'll get the output for your current partitions.

In a terminal, you can also use:

```
df -h
```

to see where those partitions are currently mounted.

Are you setting up a server that will share these drives across a network? If so, you will need to mount the partitions on the server, then use nfs to share them to other Ubuntu (Linux) clients. If you're sharing with Windows clients, you'll have to use something like samba or an ftp server. [I suggest you look at the Tutorials and Tips forum and start searching through that information as well.]("http://ubuntuforums.org/forumdisplay.php?f=100")

---

### Post by Jellax on 2010-09-28
Aha, the magical sudo :)


Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005f9be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      182401  1465136001    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x02810281

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           38002       38245     1951744   82  Linux swap / Solaris
/dev/sdb2           38246      121600   669549007    f  W95 Ext'd (LBA)
/dev/sdb3   *           1       38002   305249280   83  Linux
/dev/sdb5           38246      121600   669549006    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdc: 1500.3 GB, 1500299395072 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00026d5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182402  1465135104    7  HPFS/NTFS

---

### Post by ddnev45 on 2010-09-28
Is Ubuntu installed on one of the internal sata drives, or are they two drives specifically installed for sharing?

---

### Post by Jellax on 2010-09-28
Ubuntu is installed on sdb if Im not mistaken.

---

### Post by ddnev45 on 2010-09-29
Were all your drives attached when you installed Ubuntu, or are you adding them now?

Looks like you need to create mount points then edit your /etc/fstab file to get the setup you want.

---

### Post by sandyd on 2010-09-29
> **Jellax said:**
> Ok this is my plan.

I just installed Ubuntu 10.4 and need some help with mounting issues.
Remember, I am a total novice, I know nothing about the console, how it works etc.

I have a server with 2 internal sata drives and 2 external USB drives.
What I want to do is to make a setup of folders like this
movies
       - DVD
       - HD
       - Series
This set up of folders will be on all my drivers. I want to mount the content from USB1's HD folder to the top lever HD folder, and the same with DVD etc.
I want to do the same from USB2.

After that the folder structure should look like this:
movies
       - DVD-
             DVD1
             DVD2
       - HD-
             HD1
             HD2
And so on. Is this possible?
How can I do this?
Please note that I need really clear instructins, because I know absolutely nothing about hos anything is done in Linux. I need instructions that I more or less can copy and past and just add my labelnames of the drives.

Anyone that can help me with this will be considered a Linux god from now on :)
you have everything plugged in?
the fdisk output only shows 3 disks.
p.s. why don't you use softraid?
you can just link all your disks into one huge disk using a raid0 configuration. (Assuming you don't remove any of the drives)

---

