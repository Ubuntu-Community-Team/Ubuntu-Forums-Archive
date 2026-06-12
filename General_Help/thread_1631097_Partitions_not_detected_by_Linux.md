---
title: "Partitions not detected by Linux"
date: 2010-11-26
forum: General Help
---

### Post by rifefox on 2010-11-26
Hi.  
I need some help. I want to install Linux Mint, but it cannot detect my existing partitions.
I have a 500GB HDD, splitted in three partitions, on c: having a Win7 installed, and on d: and e: a lot of personal data.
I tried to install Linux Mint, but the installer says there is no other OS installed and there is no any partition at all. I run the Linux Mint in live mode, Gparted says:  "unallocated 465.76GiB". But when I go to Menu -> Computer then I can see each and every partition, I can mount them and browse them properly.

I tried Ubuntu 10.04 and 10.10 with the same result as described above.

Help me solve this, pls.
Thank You.

---

### Post by dino99 on 2010-11-26
you might need to resize your partition(s) to make room first


here is how to install:


use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by carl4926 on 2010-11-26
You must create an extended partition in all that free space
Then follow @dino99
and create partitons in the extended

---

### Post by rifefox on 2010-11-26
Thanks for your reply, but my problem is that the Linux installer does not see my current partitions.
Actually I know how to resize and create new partitions, but as Gparted treats my HDD as a new HDD with no existing partitions, creating new ones will obviously truncate my partitions, not to mention that there will no Grub menu as the installed Win7 is not detected. I want to keep the Win7, at least for the moment. And my HDD is full of personal data that are at risk if I begin to create new aprtitions now.

---

### Post by carl4926 on 2010-11-26
Live cd

```
fdisk -l
```

result?

---

### Post by wilee-nilee on 2010-11-26
> **rifefox said:**
> Thanks for your reply, but my problem is that the Linux installer does not see my current partitions.
Actually I know how to resize and create new partitions, but as Gparted treats my HDD as a new HDD with no existing partitions, creating new ones will obviously truncate my partitions, not to mention that there will no Grub menu as the installed Win7 is not detected. I want to keep the Win7, at least for the moment. And my HDD is full of personal data that are at risk if I begin to create new aprtitions now.

Once you resize and leave open space gparted should show the HD correctly. But it wont hurt to post the output from the command in the last post above mine first.

---

### Post by rifefox on 2010-11-26
> **carl4926 said:**
> Live cd

```
fdisk -l
```result?

There's no any result, it does not list anything. There's no error message, no any result.

Any other suggestion?

---

### Post by carl4926 on 2010-11-26
Make sure you did

```
sudo fdisk -l
```

If you get Parted Magic
Boot it up
Do you see anything in the Partition editor?

---

### Post by rifefox on 2010-11-26
sudo fdisk -l gives the following result:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3de23de2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       60802   437186342    f  W95 Ext'd (LBA)
/dev/sda5            6375       19122   102398278+   7  HPFS/NTFS
/dev/sda6           19123       55178   289617231    7  HPFS/NTFS
/dev/sda7           56394       60261    31064064   83  Linux
/dev/sda8           60262       60802     4339712   82  Linux swap / Solaris

---

### Post by WorMzy on 2010-11-26
That tells us that you have two primary partitions: one NTFS, and one extended.

In the extended partition you have: two NTFS partitions, one Linux partition, and one swap partition. Does this sound right so far?

It's unusual for the Ubuntu installer to not recognise the partitions on a disk, but not unheard of. You might want to try the alternate text-based installer, and see if that recognises your partitions. You can download the alternate installation disk iso from here: [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download).

If you decide to use the alternate installer, this may come in useful: [https://help.ubuntu.com/community/Installation/LowMemorySystems#Install%20an%20Ubuntu%20command-line%20system](https://help.ubuntu.com/community/Installation/LowMemorySystems#Install%20an%20Ubuntu%20command-line%20system)

In any case: don't worry. Your partitions are there. The Ubuntu installer not being able to see them is irrelevant. Your data is safe. (At least for the time being)

---

### Post by carl4926 on 2010-11-26
> **rifefox said:**
> sudo fdisk -l gives the following result:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3de23de2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       60802   437186342    f  W95 Ext'd (LBA)
/dev/sda5            6375       19122   102398278+   7  HPFS/NTFS
/dev/sda6           19123       55178   289617231    7  HPFS/NTFS
/dev/sda7           56394       60261    31064064   83  Linux
/dev/sda8           60262       60802     4339712   82  Linux swap / Solaris

So Linux does see your partitions.
Make sure your CD is not defective, though if you can boot to the live desktop it suggests it probably OK
[http://dl.dropbox.com/u/10573557/Ubuntu/Ubuntu-boot-menu.jpeg](http://dl.dropbox.com/u/10573557/Ubuntu/Ubuntu-boot-menu.jpeg)

At the part where the installer asks about where to install - choose the custom option to manually assign partitions.
In the following display you should be able to see the partitions you just quoted.
Double click sda7
In the resulting box, choose to Use this as ext4, to format and assign mount point as /
Swap will look after itself
Now just proceed

Does that help

---

### Post by rifefox on 2010-11-27
Yes, the Linux does see the partitions. As I mentioned before going to Menu -> Computer I can access all of my partitions.
I checked the integrity of the disk, there were no errors found. And I tried with Mint, Ubuntu 9.04, 10.04, 10.10 some of them 32bit others 64bit version. Same result.

I booted up Parted Magic:
Going to Mount Devices - it mounts everything up properly, on Mount-gtk panel every partition is showed, 
Partition Editor - opens the GParted window saying unallocated 465.76Gib,
Test Disk - Select a media: Disk /dev/sda - 500GB/465GiB ATA WDC.

> In the extended partition you have: two NTFS partitions, one Linux  partition, and one swap partition. Does this sound right so far?Yes, that's ok. 
I just can't figure out why the partition managers can't see the partitions.

I have already tried to fix the MBR from Windows7, as I thought the MBR was messed up. Didn't help.

> You might want to try the alternate text-based installerI'm going to give it try.


I'm waiting for further suggestions.

Thanks.

---

### Post by rifefox on 2010-11-29
Any idea?

---

### Post by rifefox on 2010-12-01
bump

---

### Post by carl4926 on 2010-12-02
Try this version of Parted Magic
[http://dl.dropbox.com/u/10573557/pmagic-4.5.iso](http://dl.dropbox.com/u/10573557/pmagic-4.5.iso)

Because this comment:
> I booted up Parted Magic:
Going to Mount Devices - it mounts everything up properly, on Mount-gtk panel every partition is showed, 
Partition Editor - opens the GParted window saying unallocated 465.76Gib,
Test Disk - Select a media: Disk /dev/sda - 500GB/465GiB ATA WDC.

Is crazy. Not you. I just mean it can't happening can it!
Try the PMagic above

---

### Post by Mosabama on 2010-12-02
This happened to me once... 
fdisk could see the partitions.
any GUI partitioner (like gparted) couldnt.  actually showed the whole volume as unallocated, and I think the installer runs gparted I am not sure.

the computer used to boot normally. but it seemed the partition table was corrupted.

what I did was that I downloaded a tool called testdisk-6.11.3 that runs without installing.. you can put it in a flash and boot from live cd and then use it ... it fixed my partition table and they showed again in gparted.

its not a dangerous tool as far as I know ... and its easy to use. but before you do that. do a backup of the current MBR and partition table any way:

```
dd if=/dev/sdx of=/home/username/MBR-BACKUP bs=512 count=1
```

change sdx with your volume name ... mostly sda if you have only 1 harddisk. and username with your username.
and keep the MBR-BACKUP file in a flash disk or something.
try the tool. 

good luck

---

### Post by carl4926 on 2010-12-02
Testdisk is included in Parted Magic BTW
A great app

---

### Post by Mosabama on 2010-12-02
Oh yes it is ... saved my life.

Actually didnt know that it would fix the partition table, but I though what the hell, give it a shot before I reformat my PC again and start over. it was my last hope. really great app

---

### Post by rifefox on 2010-12-03
Good to see there are members here who cares about my problem. Thanks again.

So, I booted up again Parted Magic, now version 4.5. 
You say TestDisk is great, I don't doubt that, but can you tell me what am I supposed to do with it?

I tried several options within TestDisk, neither of them helped.
I took a few screenshots, to help you figure out what my problem is:

GParted: [http://img834.imageshack.us/img834/5971/gparted0.png](http://img834.imageshack.us/img834/5971/gparted0.png)

PartitionImage: [http://img813.imageshack.us/img813/1132/partitionimage.png](http://img813.imageshack.us/img813/1132/partitionimage.png)

Mount Devices: [http://img829.imageshack.us/img829/3986/screenshot1wr.png](http://img829.imageshack.us/img829/3986/screenshot1wr.png)

In TestDisk I chose Intel/PC Partition: [http://img17.imageshack.us/img17/8075/tdintel.png](http://img17.imageshack.us/img17/8075/tdintel.png)
Is that ok?

Hidden Sectors are present: [http://img11.imageshack.us/img11/8833/tdhiddensectors.png](http://img11.imageshack.us/img11/8833/tdhiddensectors.png)

Then I choose to analyze partitions: [http://img441.imageshack.us/img441/1503/tdanalyse.png](http://img441.imageshack.us/img441/1503/tdanalyse.png)

Current partition structure: [http://img834.imageshack.us/img834/8338/tdanalyse2.png](http://img834.imageshack.us/img834/8338/tdanalyse2.png)

Quick Search Result: [http://img193.imageshack.us/img193/5137/tdquicksearchresult.png](http://img193.imageshack.us/img193/5137/tdquicksearchresult.png)

On another session of TestDisk at this step [http://img441.imageshack.us/img441/1503/tdanalyse.png](http://img441.imageshack.us/img441/1503/tdanalyse.png)
 I selected MBR Code, then answered yes to the question to overwrite the MBR. Following this my Win7 wasn't able to boot up, so I needed to make a repair from the Win7 installer DVD. This didn't change anything on this issue described in this thread.


That's all for now. If further pieces of information are required let me know.

Any help is highly appreciated. Thank You.

---

### Post by rifefox on 2010-12-03
> **neelamsaxena said:**
> I ran into a problem of duplicate files and someone told me about [www.dublicateFilesDeleter.com]("http://www.dublicateFilesDeleter.com")

I think you missed the thread with this post.

---

### Post by WorMzy on 2010-12-03
I think that's a spambot.

---

### Post by rifefox on 2010-12-04
Help!

---

### Post by WorMzy on 2010-12-04
Have you tried that alternate installer I posted a link to?

---

### Post by oldfred on 2010-12-04
I have had gparted not see a drive, but after running chkdsk on the NTFS partition it would see it. My XP would boot before & after without complaint.

Run chkdsk on any NTFS partitions even if they currently work.

Another alternative:
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by rifefox on 2010-12-06
> **WorMzy said:**
> Have you tried that alternate installer I posted a link to?


Yes, I have.

I chose partitioning method: manual.

"Overview of your currently configured partitions:
-Guided partitioning
-SCSI3 (0,0,0)(sda) - 500.1GB ATA
-Undo changes
-Finish Partitioning"



No partitions detected...
[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

---

### Post by rifefox on 2010-12-11
Problem solved.

It seems my problem was a tricky one, I mean I don't know what caused it.

I deleted every ext3 partition on my HD, and attached the unallocated space to one of my NTFS partitions.

Now the Gparted detects all 3 NTFS partitions and the installed Win7. Now everything is ready to setup Ubuntu.

Next time I'll login here using my brand new Ubuntu 10.10.

:)

Thanx everyone.

---

