---
title: "Resizing partitions"
date: 2010-11-23
forum: General Help
---

### Post by M1ke on 2010-11-23
Hi all. I'm running a dual-boot system and foolishly gave Windows 7 little space on the disk. Given that my Ubuntu installation has enormous amounts of unused drive space, I wondered if there was a way to expand the size of the Windows partition perhaps using gparted on the Ubuntu LiveCD without having to fully reinstall both OS?

In the past I've used Windows' disk management tools to shrink its partition, but here I want to do the opposite and the management tools in Windows itself just aren't up to the job.

I'd like to donate about 50GB of my /home partition to Windows. Does anyone have any experience doing this? Is it possible without reinstalling one or both OS?

---

### Post by sikander3786 on 2010-11-23
Please post the output of,

```
sudo fdisk -lu
```

It will tell us about your partition setup and whether the space from /home can be added to Windows or not.

And don't use any Windows tools to resize Linux partitions. Windows doesn't recognize ext filesystems so it just might result in a Loss.

---

### Post by M1ke on 2010-11-23
Output of the command:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdbdf45b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   125831167    62812160    7  HPFS/NTFS
/dev/sda3       125831168   213727231    43948032   83  Linux
/dev/sda4       213729278   976773119   381521921    5  Extended
/dev/sda5       213729280   222515199     4392960   82  Linux swap / Solaris
/dev/sda6       222517248   976773119   377127936   83  Linux

```

Seems I want to reallocate space from sda6 (/home) to sda2 (Windows' partition).

---

### Post by M1ke on 2010-11-23
As a follow-up question, what in that output points to whether I can reallocate the drive space?

---

### Post by Dr. C on 2010-11-23
The simplest way is to boot from the live CD and run GParted. 
First shrink /dev/sda6 by 50GB and move /dev/sda6 so the the free space is on the side closest to /dev/sda2. Then move the other partitions so that 50GB is next to /dev/sda2. You will need to set swap off to move the swap partition. Finally grow /dev/sda2 into the free space 

After this is completed boot into Windows 7 and run chkdsk /F from a Windows command prompt on the resized Windows partition.

---

### Post by oldfred on 2010-11-24
What the fdisk shows is that the partition you want to shrink is nowhere near where you want it. You have to shrink sda6 and move it right, move swap right & shrink the extended partition, then move sda3 right. Only then you can expand sda2. 

You have just moved almost everything on your drive. Have good backups and do it a step at a time. With reboots to make sure everything is ok. If you move things too much you may have to reinstall grub. UUID should not change with just a move, but if they do then you also have to edit fstab. All of this is doable, just a lot of work.

Note that some of the moves with gparted may take hours, do not interrupt or you will corrupt system.

---

### Post by Herman on 2010-11-24
[IMG]http://members.iinet.net.au/%7Eherman546/p22/012.png[/IMG]

... and be sure to remember to remove the check mark from the 'round to cylinders' checkbox in GParted before you resize your Windows partition.
If you forget, GParted will dutifully 'move' the entire partition for you and not only it will take an excessively long time, (because that's a big job), but it will also result in your Windows boot loader requiring repairs when you're done. If you're lucky it will only require a minor repair, but sometimes it could need a bit more fiddling around and rebooting more than once. It's easier just to remember to remove the check mark.

I think there might be a more modern version of that checkbox but I'm not sure yet, I think I saw a screencap of one that said 'SSD alignment', or something like that. 
EDIT: Maverick Meerkat Live CD's GParted has an 'Align to:' spinbox that seems to be set to MiB by default. I haven't tested it yet, but it seems like a great idea.

GParted can safely resize Windows partitions, it's better than Windows Disk Management, actually, (at least in my opinion), but some people use ancient GParted versions that pre-date Windows Vista and 7 and don't have the 'round to cylinders checkbox', and others are not aware of what the check box is for. :)

---

### Post by M1ke on 2010-11-24
Some very detailed responses here, thank you very much everyone! Sounds like quite a job so I'll start it when I have plenty of time to devote to it and come back if I run in to any issues.

Thanks!

---

### Post by M1ke on 2010-11-24
...And issues I did indeed run in to :(

Moving and resizing sda6 was no trouble, but on trying to move sda5 (swap I believe) the process failed saying "invalid partition table on /dev/sda -- wrong signature 0"

On closing that box I'm met with the attached image in gparted. I feel quite sure that's rather bad news, so I'm gonna reboot and see if I can access either OS.

Edit: Okay, grub presents me with the option of booting Ubuntu or Windows, but Ubuntu now cannot find the /home partition. I'm given the choice of waiting, skipping the mount process or trying it manually (which presents a terminal but I don't know what I'm doing from there). 

Following the reboot gparted still views the entire disk as unallocated space, and from the LiveCD I cannot view the large, missing /home partition.

Windows appears unharmed and boots normally, though interestingly can now see a large amount of "free space" in the disk manager that can't view ext4 filesystems.

Has my /home partition now disappeared in to the void, or does the "invalid partition table" message perhaps mean it is still there but is presently inaccessible to Ubuntu or the LiveCD gparted?

---

### Post by oldfred on 2010-11-24
I would see what test disk shows.

repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Some other things to try
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by M1ke on 2010-11-25
Thank you for taking the time to help. Sadly though as I dug through the links and read up on test disk it soon became clear that reinstalling both OS from scratch was going to be quicker than trying to salvage what was left.

Still, on the bright side rolling back to Lucid has fixed the odd little bug I had with Maverick, so it's not a total loss.

Cheers!

---

### Post by perspectoff on 2010-11-25
> **M1ke said:**
> ...And issues I did indeed run in to :(

Moving and resizing sda6 was no trouble, but on trying to move sda5 (swap I believe) the process failed saying "invalid partition table on /dev/sda -- wrong signature 0"

On closing that box I'm met with the attached image in gparted. I feel quite sure that's rather bad news, so I'm gonna reboot and see if I can access either OS.

Edit: Okay, grub presents me with the option of booting Ubuntu or Windows, but Ubuntu now cannot find the /home partition. I'm given the choice of waiting, skipping the mount process or trying it manually (which presents a terminal but I don't know what I'm doing from there). 

Following the reboot gparted still views the entire disk as unallocated space, and from the LiveCD I cannot view the large, missing /home partition.

Windows appears unharmed and boots normally, though interestingly can now see a large amount of "free space" in the disk manager that can't view ext4 filesystems.

Has my /home partition now disappeared in to the void, or does the "invalid partition table" message perhaps mean it is still there but is presently inaccessible to Ubuntu or the LiveCD gparted?

Ooops. Somehow you reformatted your entire disk. Have to reinstall from scratch once you do that.

---

