---
title: "Strange behaviour with HD and CD/DVD drives"
date: 2009-08-05
forum: General Help
---

### Post by budgie9 on 2009-08-05
Since a recent update, I don't actually know which one,about 4 weeks back, which may not be related either.  I have lost the proper function of the DVD\CD-WR units in my computer. I can write a disk using K3b or Brasero, but they always come back as locked disks, (not appendable) no matter the amount of files on the disks. I also seem to have lost the ability to Drag and Drop files to DVD\CD drives. Even if the disk is formatted as 'appendable' in another computer. The drives also lock up not enabling me to eject the disks when using the above programs or after reading them in Nautilus. I get a 'Not Mounted' message each time. The only way to eject the disks is to restart the computer. It is as if the drives are no longer a part of the computer but can be seen in Nautilus I have moved these DVD\CD-WR drives to a second computer and they work as one would expect. Writing and reading and ejecting of the disks. One can rule out a fault witht he drives. That computer by the way has Ubuntu 8.04 on it.

I am also seeing some strange locking of files on the HD partitions. (All those files have a lock over the icon.)  I found this happening on the two hard disks. It sometimes shows up in the File System folder as well, Leaving me no alternative but to restart the computer so as to access some of these files again. Though it is most frequently in my own files in other partitions.
I am so far unable to resolve this issue though it is not for the want of trying. I have re-built the Fstab file numerous times, which MAY resolve the issue for a day or so and provided there is no DVD\CD access,but as soon as I try using the DVD\CD the problem can but not always return. I am using Ubuntu 8.10 and have thought to upgrade, but before I do I wnat to know a solution to this on going problem. 
Has anyone else experienced these starnge things or can anyone help me resolve them.
I have looked through the forums and can find somethings but nothing that seems to actually resolve the issues.

UUID=6c014b16-1e36-44e5-a635-bd1742908623	/	ext3	defaults	0	1
UUID=2f0c38b3-1d2f-4f19-a2db-e4427740af2d	/home	ext3	defaults	0	2

UUID=49E7-4818	/media/sda7	vfat	defaults	0	0
UUID=49E7-4819	/media/sda8	vfat	defaults	0	0
UUID=ae28bca9-ba07-4aa0-9699-4fee8b1eb0d1	swap	swap	sw	0	0
UUID=49E7-4AC8	/media/sdb5	vfat	defaults	0	0
UUID=49E7-4AC9	/media/sdb6	vfat	defaults	0	0
UUID=4A77-1635	/media/sdb7	vfat	defaults	0	0
UUID=49E7-4ACC	/media/sdb8	vfat	defaults	0	0
UUID=49E7-4ACD	/media/sdb9	vfat	defaults	0	0
/dev/scd0	/media/cdrom0	udf,iso9660 noauto 0	0
/dev/scd1	/media/cdrom1	udf,iso9660 noauto 0	0

---

### Post by budgie9 on 2009-08-06
Is it a difficult question? I would think someone has some idea what is going on. Can anybody help with this problem?

---

