---
title: "External Hard Disk Mount"
date: 2010-05-19
forum: General Help
---

### Post by momo2 on 2010-05-19
Hi All, 

Actually, I Have An External Hard Disk "Western Digital" It Is Protected By A Password .. !
I Want To Mount In But I Don't Know How  !!

[IMG]http://imgur.com/8Fz31.png[/IMG]

I Just Installed My Ubuntu And I Need To Open My HD .. One More Thing :] I'm A CCNA Candidate Is There Any SoftWare or Simulator Like "Packet Tracer For Ubuntu .. !

---

### Post by CharlesA on 2010-05-19
It's already mounted.

---

### Post by momo2 on 2010-05-19
Ah Ok My Bad .. But The Thing Is The HD Is Locked And To Unlock The HD In Windows Is To Click On UNLOCK.EXE Then Entering The UserName and Password .. How Do I Do That With Ubuntu !! 

*I'LL TRY TO EDIT THE TITLE

---

### Post by CharlesA on 2010-05-19
Probably won't work. Are all the files stored in a specific folder on the drive?

---

### Post by Darkness Des on 2010-05-19
You could install Wine. It works on most all EXE files. I would suggest other methods I know, such as changing permissions on it, but I don't know how it would react seeing as it's locked by an Executable and not just flags. If Wine can't open it, then I recommend going back into Windows and removing the password on it.
Wine can be found at
[http://www.winehq.org/](http://www.winehq.org/)

Just follow their installation guide.

---

### Post by momo2 on 2010-05-19
> Probably won't work. Are all the files stored in a specific folder on  the drive?

i've partetioned the HD to 3 drivers and i want them all 

> You could install Wine. It works on most all EXE files. I would suggest  other methods I know, such as changing permissions on it, but I don't  know how it would react seeing as it's locked by an Executable and not  just flags. If Wine can't open it, then I recommend going back into  Windows and removing the password on it.
Wine can be found at
[http://www.winehq.org/](http://www.winehq.org/)

Just follow their installation guide.

i'll try and hopefully it works, i'll be back with the outcome

---

### Post by CharlesA on 2010-05-19
> **momo2 said:**
> i've partetioned the HD to 3 drivers and i want them all 

I see four drives there. New Volume, 125GB File System, Music and WD SmartWare.

Try running this in a terminal:

```
sudo fdisk -l
```

---

### Post by momo2 on 2010-05-19
^

this is the outcome of the command you posted 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe2fe76b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1534976    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       15362   121854976    7  HPFS/NTFS
/dev/sda3           15362       29096   110318592    7  HPFS/NTFS
/dev/sda4           29096       30402    10485760    f  W95 Ext'd (LBA)
/dev/sda5           29096       30402    10484736    7  HPFS/NTFS

----------------------------------------------------------------------------------------------

i tried with wine it says--  wine: cannot find '/media/WD'

---

### Post by CharlesA on 2010-05-19
Hrm, in that case, please post the output of this:

```
mount -l
```

---

