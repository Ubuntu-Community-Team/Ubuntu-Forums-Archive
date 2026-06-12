---
title: "Ubuntu server backup?"
date: 2009-11-13
forum: General Help
---

### Post by ubuntüser on 2009-11-13
I have an Ubuntu Server 9.10 (with GUI available if needed). It is running 3 HDDs. 
160 GB IDE HDD - this is OS drive
1TB SATA }\
           -- These two form a RAID 1 array using mdadm linux software raid
1TB SATA }/

So, what I want to do: I'm not worried about the RAID drives failing. But what about the OS drive?

The OS drive has ONLY 3GB used, so is there any way to make a full backup? Like I can pop a DVD in, and EVERYTHING is restored to how it was, including linux software raid, webserver, etc etc?

I don't really want to just back up directories - all my data is on RAID partition. But my OS and server and mysql database is on OS drive.

Thanks,
ubuntüser

EDIT: Is sbackup good? I found this tut: [http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)
But command line would be better, true?

I want something that'll allow me to restore easily when my OS drive is dead and gone.

---

### Post by undecim on 2009-11-13
Since it's just 3GB, why don't you set up a cron job to make a backup on the RAID drives? Take a look at rsync.

As far as restoring if the OS drive is gone, you will need to replace the drive and use a livecd to move the files to the new drive and reinstall the bootloader.

---

### Post by ubuntüser on 2009-11-14
Is there any easier way? Like burning a DVD that is one click restore (or few clicks)?

---

### Post by Olav on 2009-11-14
> **ubuntüser said:**
> Is there any easier way? Like burning a DVD that is one click restore (or few clicks)?

You could use imaging software (like [partimage]("http://www.partimage.org/")) to periodically take a snapshot of your disk that you can restore. It will require you to take your server offline for the time it takes to make the image (would be very short with just 3 GB). You could backup to DVD-RW or an USB stick or something.

I disagree with not backing up the data on your RAID set. RAID is not a substitute for backups. There are many causes of data loss, most have nothing to do with failing hardware.

---

### Post by ubuntüser on 2009-11-14
My server can be taken offline, because its just a home server. I don't really know where to backup my data on the RAID drive... Maybe on an external disk, and the really important stuff on DVDs.

Thanks for that software, looks better than sbackup.

---

### Post by Olav on 2009-11-15
> **ubuntüser said:**
> My server can be taken offline, because its just a home server. I don't really know where to backup my data on the RAID drive... Maybe on an external disk, and the really important stuff on DVDs.
If it's a home server I would not worry about all the downloaded music and video files... If you are like most people that is 90% of your data that you don't need to backup 8)

Personal documents and photos are always more important. An external disk dedicated to this would be a good idea, perhaps combined with the [Back in Time]("http://backintime.le-web.org/") incremental backup program. And you can always make DVDs just to be sure, as well.

> Thanks for that software, looks better than sbackup.
I don't know sbackup but partimage has saved my you-know-what a couple of times already. I have used it professionally and in more informal situations. Without a lot of computer background it may look complicated at first but it is really not. Just take some time to make sure you know what it does and that you can do a restore.

BTW: I most often use it from the [System Rescue CD]("http://www.sysresccd.org/") which is a bootable CD with many helpful utilities. Lots of information can be found on both websites.

---

