---
title: "Ubuntu can't see windows 7 drive"
date: 2012-05-06
forum: General Help
---

### Post by nessport20 on 2012-05-06
Hey,

I just recently installed Ubuntu 12.04. When I restarted my computer and I logged on, I tied to find my Windows 7 drive in Nautilus but it wasn't listed.

I have tried stuff like ntfs-config, editing fstab etc. however neither of these give me access to my Windows 7 internal HDD. I have been able to access NTFS drives as I was able to read/write to an NTFS external drive.

I have been able to use 'sudo mount' through terminal but I want to be able to explore it via Nautilus just like I could on 11.10 and lower. 

I ran 'sudo fdisk -l' and it shows my NTFS Windows drive fine.

I would like to have the latest version of Ubuntu but if it means no access to Windows then I will just go back to 11.10

Any ideas?

---

### Post by Drlbpgtdeomt on 2012-05-06
Yeah,I have the same problem with you.I am so upset...

---

### Post by oldfred on 2012-05-06
@   	nessport20
Please post this:
```

sudo fdisk -lu
```

@   	Drlbpgtdeomt
If your problem is not exactly the same please start your own thread as trying to manage two different solutions in one thread starts to get difficult on who is doing what.

---

### Post by nessport20 on 2012-05-12
I get:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaef40f72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976771055   488384504    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00003b81

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    41945087    20971520   83  Linux
/dev/sdb2        41945088   304193535   131124224   83  Linux
/dev/sdb3       304193536   312580095     4193280    5  Extended
/dev/sdb5       304195584   312580095     4192256   82  Linux swap / Solaris

---

### Post by wilee-nilee on 2012-05-12
> **nessport20 said:**
> I get:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaef40f72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976771055   488384504    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00003b81

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    41945087    20971520   83  Linux
/dev/sdb2        41945088   304193535   131124224   83  Linux
/dev/sdb3       304193536   312580095     4193280    5  Extended
/dev/sdb5       304195584   312580095     4192256   82  Linux swap / Solaris


Open the disk utility and see if it is showing, better yet gparted, you might need a chkdsk run.

Assuming the sda HD with one partition is the windows install.

---

### Post by nessport20 on 2012-05-12
> **wilee-nilee said:**
> Open the disk utility and see if it is showing, better yet gparted, you might need a chkdsk run.

Assuming the sda HD with one partition is the windows install.

GParted shows Windows HDD, which is sda1.

I have managed to found a solution to my problem, as it turns out I didn't edit fstab correctly.

I now have my windows drive (/dev/sda1) auto-mounting to /media/Windows7.

Thanks for your help.

---

### Post by wilee-nilee on 2012-05-12
> **nessport20 said:**
> GParted shows Windows HDD, which is sda1.

I have found a solution to my problem, as it turns out I didn't edit fstab correctly. 

I now have my windows drive (/dev/sda1) auto-mounting to /media/Windows7.

Ah you're one of those auto-mounters eh, glad you have it fixed. ;)

---

