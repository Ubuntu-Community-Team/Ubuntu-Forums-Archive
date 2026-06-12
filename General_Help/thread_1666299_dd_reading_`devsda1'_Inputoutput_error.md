---
title: "dd: reading `/dev/sda1': Input/output error"
date: 2011-01-13
forum: General Help
---

### Post by ibod on 2011-01-13
Hi all,

I was trying to copy from a hard drive, to an image file using :-

```


sudo dd if=/dev/sda1 of=/media/Iomega\ HDD/backup/pc130111.img


```_Some info about the hard drive._
The hard drive I am trying to copy is formatted ntfs and has XP on it. 

It is about 6 years old and is having problems.
When booted from a 10.4 live CD. Most of the time the hard drive reports that it is not a S.M.A.R.T. capable drive.
Once, it was, able to read the SMART data and reported OK except 3 bad sectors.

From the above and especially the "smart / no  smart" I am assuming that there is likely a controller problem on the drive as well as the bad sectors.

dd exits with the following error :-

```


ubuntu@ubuntu:~$ sudo dd if=/dev/sda1 of=/media/Iomega\ HDD/backup/pc130111.img 
dd: reading `/dev/sda1': Input/output error 
6406224+0 records in 
6406224+0 records out 
3279986688 bytes (3.3 GB) copied, 432.584 s, 7.6 MB/s 
ubuntu@ubuntu:~$ 


```The windows system still runs, but its time for an .img and a new drive, before it dies.

What do I need to do here to get a usable copy of this drive ?

---

### Post by GNU-Cody on 2011-01-13
I wouldn't recommend imaging an OS from a HDD with unrepaired/unflagged bad sectors on it as the corrupted data will be imaged as well. While the corrupted data won't hurt the new drive that it's transferred to, it could bring varying instabilities with it to the new system. I would recommend saving any files off of the bad drive that you want by utilizing an Ubuntu 10.04 or 8.04 live CD as the boot drive and then doing a clean install of whatever OS on to the new HDD. After that you can easily restore the backed up files to the new system and there won't be any worries about OS errors caused by the bad sectors on the old HDD. 
 However if you really need to image that drive off to another then I would recommend using Clonezilla (available at [**http://www.clonezilla.org/**]("http://www.clonezilla.org/")). Clonezilla won't cure the ills of the damaged drive but it may work through or around those errors. Other than that you can instruct "dd" to ignore errors with the "noerrors" option. See the "dd" man pages ("man dd" in linux terminal) for precise usage. Good luck!

---

### Post by ibod on 2011-01-13
> **GNU-Cody said:**
> I wouldn't recommend imaging an OS from a HDD with unrepaired/unflagged bad sectors on it as the corrupted data will be imaged as well. While the corrupted data won't hurt the new drive that it's transferred to, it could bring varying instabilities with it to the new system. I would recommend saving any files off of the bad drive that you want by utilizing an Ubuntu 10.04 or 8.04 live CD as the boot drive and then doing a clean install of whatever OS on to the new HDD. After that you can easily restore the backed up files to the new system and there won't be any worries about OS errors caused by the bad sectors on the old HDD. 
 However if you really need to image that drive off to another then I would recommend using Clonezilla (available at [**http://www.clonezilla.org/**]("http://www.clonezilla.org/")). Clonezilla won't cure the ills of the damaged drive but it may work through or around those errors. Other than that you can instruct "dd" to ignore errors with the "noerrors" option. See the "dd" man pages ("man dd" in linux terminal) for precise usage. Good luck!

Hi GNU-Cody

Thanks for your reply, I think you are correct about the instability of any operating system cloned from this drive. I guess its a dead loss, I have all the installation CD's and a good set of backup DVD's of all the personal files. 

so unless any one comes up with a good way to clean it up (have done a chkdsk /p in windows recovery) then its going to be a new drive and a reload.

Have also tried :-

```


dd if=...  of=... conv=noerror,sync


```

this results in a lot of errors, its only up to 3.3GB and there are more errors than the terminal can buffer.

---

### Post by efflandt on 2011-01-13
dd (or clonezilla) would tend to choke when they do a sector by sector copy and reach bad sectors they cannot read at all.  Acronis running from Windows can image image partitions with bad sectors as long as you do **chkdsk /f** from Windows to fix and lock out the bad sectors first.  Some drive manufacturers have their own free version of Acronis that works with their drives, at least wdc.com (Western Digital) and seagate.com (for Seagate and Maxtor drives).  Maybe different sites in the UK.

I used that to image a WD WinXP laptop drive with bad sectors (in a USB enclosure on another PC) for the warranty replacement drive.

---

### Post by ibod on 2011-01-15
> **efflandt said:**
> dd (or clonezilla) would tend to choke when they do a sector by sector copy and reach bad sectors they cannot read at all.  Acronis running from Windows can image image partitions with bad sectors as long as you do **chkdsk /f** from Windows to fix and lock out the bad sectors first.  Some drive manufacturers have their own free version of Acronis that works with their drives, at least wdc.com (Western Digital) and seagate.com (for Seagate and Maxtor drives).  Maybe different sites in the UK.

I used that to image a WD WinXP laptop drive with bad sectors (in a USB enclosure on another PC) for the warranty replacement drive.


Thanks

I tried the chkdsk /f but it did not find anything 

Then re-run the dd clone all the errors are around the same area on the drive I suspect the same sector. 

I think the drive knows this sector is bad but has not relocated it yet, and that is why i have all the errors.

The rest of the dd clone runs without errors.

does anyone know if it takes time for a drive to re-allocate a bad sector ?


scrapped the drive and did a reload on new drive :-)

---

