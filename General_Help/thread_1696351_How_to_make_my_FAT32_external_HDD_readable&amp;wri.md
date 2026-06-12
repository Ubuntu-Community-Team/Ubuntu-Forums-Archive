---
title: "How to make my FAT32 external HDD readable&amp;writable"
date: 2011-02-27
forum: General Help
---

### Post by erginero on 2011-02-27
My external HDD became read only, and even not readable for a folder in it. Until now I had no problem with reading/writing on it but at my last mounting it get unwritable. When I right-click and try to change rights it says you cant it's a read only file system...
I am new with linux, can you please help me :confused:

---

### Post by erginero on 2011-03-01
Did I write to wrong place ? Nobody knows? 
Here it is what I have:

/dev/sdc6 on /media/4AF0-8971 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc5 on /media/95E1-133A type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

How can I change it??

---

### Post by Timos798 on 2011-03-01
Hey there and welcome to the forums!
Have you tried formatting it to NTFS? That seems to solve most problems, but if you dod ecide to format, remember that it deletes EVERYTHING on the drive you are formatting.

---

### Post by erginero on 2011-03-01
Thank you for your welcome, 
To answer I can not format because:
- I dont want to loose everything
- I need FAT32 to use it with my Media Player.

On the other hand I'm sure that it is only a software problem because my mediaplayer can see the files that are even not readable in PC (some folders are closed to read&write). I also checked it under XP same problem there...

---

### Post by vanadium on 2011-03-01
I can second that FAT32 is a highly unreliable file system that I would recommend only for USB sticks. Yet reformatting does not solve your immediate problem.

What troubles me is that the output you show does not indicate that the file systems are mounted as read only: they are mounted as read/write.

They are mounted with full permissions for user 1000, which on an Ubuntu system is the first account that was created on that system. So make sure you are actually logged in as user 1000 before suspecting a problem with the drive (run the command "id").

The very first thing you should do in any case is check the integrity of your file system. Chances are 90% that your issue is caused by problems with the FAT file system. And I can predict you that in that case a number of the files on the system will be corrupt already.

I do not know which drive is causing the trouble, but it does not harm to check both drives. Anyone should regularly check the file system of their drives, yet few people actually do that until it is almost too late.

Open a command terminal, and perform following commands. The commands will unmount the drives and perform a diagnostic check. For now, it will just be a check. No correction will be done if there are problems. Post the output back here.

```

sudo umount /dev/sdc5
sudo umount /dev/sdc6
sudo dosfsck /dev/sdc5
sudo dosfsck /dev/sdc6

```
The two last commands will yield health reports about your drives. If there is an issue, you will need to rerun the command with the option to do repairs. Since you are not an expert, simply use the -a, "automatic" option, for example:

```

sudo dosfsck -a /dev/sdc5

```
If unsure, then first post the output of the first commands and await our advise.

---

### Post by erginero on 2011-03-01
Hi, I did, it gave: 

onur@onur:~$ sudo umount /dev/sdc5
[sudo] password for onur: 
onur@onur:~$ sudo umount /dev/sdc5
umount: /dev/sdc5: ba&#287;lanmad&#305;
onur@onur:~$ sudo umount /dev/sdc6
onur@onur:~$ 
onur@onur:~$ sudo umount /dev/sdc6
umount: /dev/sdc6: ba&#287;lanmad&#305;
onur@onur:~$ sudo dosfsck /dev/sdc5
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00, 71:20/00, 72:20/00, 73:20/00, 74:20/00, 75:20/00, 76:20/00
  , 77:20/00, 78:20/00, 79:20/00, 80:20/00, 81:20/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 3
/dev/sdc5: 9965 files, 2579931/3474210 clusters
onur@onur:~$ sudo dosfsck /dev/sdc6
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  28:3f/14, 29:00/dc, 30:00/41, 31:00/0d, 65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 3
Orphaned long file name part "r_-_The End(fromage_edit).mp3.part"
1: Delete.
2: Leave it.
? 1
/Film/diger/Belgesel
  Contains a free cluster (3138304). Assuming EOF.
Reclaimed 178737 unused clusters (5856854016 bytes).
Free cluster summary wrong (1609732 vs. really 1788469)
1) Correct
2) Don't correct
? 2
Leaving file system unchanged.
/dev/sdc6: 10280 files, 4501198/6289667 clusters
onur@onur:~$

---

### Post by vanadium on 2011-03-01
Both partitions show the error of the boot sector and its backup being different. This might not be an important issue for data disks. I would probably select to copy the backup over the boot sector.

sdc5 is not giving file system errors. This is probably not the partition you are having trouble with.

sdc6 gives some errors, but I would guess it is not quite severe and affects only one or a few files that have not been correctly written/closed. I am not sure if that could have caused your issue. Anyway, let dosfsck automatically perform the reparations with the command

```

sudo dosfsck -a /dev/sdc6

```

Run the same command on /dev/sdc5: it will not harm and you can correct the boot sector problem.

Consider updating the backup of your data and reformat the partitions to a more reliable file system. ext3 or ext4 if you are using the drive solely with linux, ntfs if this drive is also being used with MS Windows.

If after this, your issue has not been solved, we will need to look further for the actual cause of your issue.

---

### Post by erginero on 2011-03-01
Hello Vanadium, 
I did as you said, it gives: 

onur@onur:~$ sudo dosfsck -a /dev/sdd5
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00, 71:20/00, 72:20/00, 73:20/00, 74:20/00, 75:20/00, 76:20/00
  , 77:20/00, 78:20/00, 79:20/00, 80:20/00, 81:20/00
  Not automatically fixing this.
/dev/sdd5: 9965 files, 2579931/3474210 clusters
onur@onur:~$ sudo dosfsck -a /dev/sdd6
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  28:3f/14, 29:00/dc, 30:00/41, 31:00/0d, 65:01/00
  Not automatically fixing this.
Orphaned long file name part "r_-_The End(fromage_edit).mp3.part"
  Auto-deleting.
/Film/diger/Belgesel
  Contains a free cluster (3138304). Assuming EOF.
Unable to create unique name

THEN I tried to do it manually: 

onur@onur:~$ sudo umount /dev/sdd5
onur@onur:~$ sudo umount /dev/sdd6
onur@onur:~$ sudo dosfsck /dev/sdd5
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00, 71:20/00, 72:20/00, 73:20/00, 74:20/00, 75:20/00, 76:20/00
  , 77:20/00, 78:20/00, 79:20/00, 80:20/00, 81:20/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 2
Leaving file system unchanged.
/dev/sdd5: 9965 files, 2579931/3474210 clusters
onur@onur:~$ sudo dosfsck /dev/sdd6
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  28:3f/14, 29:00/dc, 30:00/41, 31:00/0d, 65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 2
Orphaned long file name part "r_-_The End(fromage_edit).mp3.part"
1: Delete.
2: Leave it.
? 1
/Film/diger/Belgesel [FONT=Arial]* [SIZE=1][COLOR=DimGray]"=>>  FYI the folder /Film/diger/Belgesel is not readable, cant see Belgesel folder even its readable in my player." [/COLOR][/SIZE]*[/FONT]
  Contains a free cluster (3138304). Assuming EOF.
Reclaimed 178737 unused clusters (5856854016 bytes).
Free cluster summary wrong (1609732 vs. really 1788469)
1) Correct
2) Don't correct
? 1
Leaving file system unchanged.
/dev/sdd6: 10280 files, 4501198/6289667 clusters

As you see, couldn't fix. I mounted again and checked but same problem persist.

---

### Post by vanadium on 2011-03-02
Try again with -a option, else try with MS Windows. If all fails, you will need to reformat that partition.

---

### Post by erginero on 2011-03-06
Hello,
I reformatted complete drive, divided into 3 partitions: FAT32, ext4, NTFS, I will use each partition for different purposes. Now everything looks fine.
Thanks.

---

