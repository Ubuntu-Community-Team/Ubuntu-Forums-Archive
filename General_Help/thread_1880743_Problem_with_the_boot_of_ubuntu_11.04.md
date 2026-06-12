---
title: "Problem with the boot of ubuntu 11.04"
date: 2011-11-14
forum: General Help
---

### Post by Riuzaki90 on 2011-11-14
Hi guys sorry for my bad english(I'm italian)...
this morning when I've opened my asus K61IC I had this message:
> Reboot and select the proper devide or insert boot media in selectedI've already tried with the order of boot devide in the bios manager but nothing changes...
now I'm on live cd UBUNTU 9.10 and I'm tryng to understand why I've this problem ...
first of all I've to say that I've an hard disk of 500 GB and I've a double partition with 255gb WINDOWS 7 and 245gb UBUNTU 11.04...
from the gparted livecd i can see this
[IMG]http://img198.imageshack.us/img198/6232/screenshotdvus.png[/IMG]
and if I try to digit cat /etc/fstab
this is the result: 
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
and this is in cat dev:
[IMG]http://img841.imageshack.us/img841/4093/screenshot1qo.png[/IMG]
is there a way to reallocate my harddrive?...it's really unbealivable this thing that's appened....-.-

---

### Post by wowcolombia1 on 2011-11-14
Im not sure but maybe the problem is that you have a disc inside your computer so install something,that happends to me some times

---

### Post by Riuzaki90 on 2011-11-14
So I've lost all my data? is there a way to save my data? please help me...I've a lot of university file and documents saved in it...

---

### Post by coffeecat on 2011-11-14
> **Riuzaki90 said:**
> So I've lost all my data?

We need to do some more investigation before coming to a conclusion.

First - the /etc/fstab you posted is from the live CD session and is not relevant.

The "unallocated" that you see in the Gparted window probably means one of two things. Either that there is a partition table inconsistency which confuses Gparted, but that the partitions are still there. Or that the partitions have been deleted or that the partition table has been deleted. If the first, it's a relatively straightforward fix. If the second, it's more complicated but you should be able to rescue your data, and possibly even your partitions.

By the way, if someone tells you to use testdisk before you have finished investigating - **don't!** You may or may not need to use testdisk but you need to see exactly what the problem is first.

Boot up the live Ubuntu CD, choose 'try Ubuntu' to get to the live desktop, ensure you are connected to the internet, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar. 

That will give us an overview of your system and hopefully why you are seeing this problem.

---

### Post by Riuzaki90 on 2011-11-14
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No known boot loader is installed in the MBR of /dev/sda.

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda (Sun disk label): 255 heads, 63 sectors, 60801 cylinders
Units = sectors of 1 * 512 bytes

   Device Flag    Start       End    Blocks   Id  System

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.
/dev/sda4                   0 3,201,957,887 3,201,957,888   0 Empty

/dev/sda4 ends after the last sector of /dev/sda

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (rw)
/dev/sr0         /cdrom                   iso9660    (rw)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sda

00000000  47 4e 55 20 50 61 72 74  65 64 20 43 75 73 74 6f  |GNU Parted Custo|
00000010  6d 20 63 79 6c 20 36 30  38 30 31 20 61 6c 74 20  |m cyl 60801 alt |
00000020  30 20 68 64 20 32 35 35  20 73 65 63 20 36 33 00  |0 hd 255 sec 63.|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 01 00 00 00 00  00 00 00 00 00 08 00 00  |................|
00000090  00 00 00 00 00 00 00 05  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 60 0d de ee  |............`...|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 15 18 ed 81  00 00 00 00 00 00 00 01  |................|
000001b0  ed 81 00 00 00 ff 00 3f  00 00 00 00 00 00 00 00  |.......?........|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  3a 38 4c 41 00 00 00 00  00 00 00 00 00 00 00 00  |:8LA............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 da be 20 c1  |.............. .|
00000200

Unknown BootLoader on sda4



=============================== StdErr Messages: ===============================

hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory

```

---

### Post by coffeecat on 2011-11-14
That looks serious. Something has happened to the whole of the mbr, not just the approx 440 bytes that contains the bootloader, but the partition table as well. If the rest of the hard drive is uncorrupted it should be possible to restore your partitions, but I would like to get some other opinions first. You need to proceed cautiously.

In the meantime, please boot up with the Ubuntu live CD, open a terminal and run this command:

```
sudo sfdisk -d /dev/sda > Desktop/pt.txt
```

That will write a small text file, pt.txt, to the live desktop. Please post the contents of this between [noparse]```
 and 
```[/noparse] tags. It probably won't tell us more than we know already but let's see it for completion.

I'm going to pm 3 forum friends to ask them to have a look too. Please be patient. They are in different time zones and may be offline at the moment.

---

### Post by Riuzaki90 on 2011-11-14
thank you so much for your help :) 

```
root@ubuntu:/home/ubuntu/Desktop# sudo sfdisk -d /dev/sda > pt.txt

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sda: unrecognized partition table type
No partitions found

```

this is the output of this command...I mean that there'snt the partition at all animore...but I don't understand why ...because first of the boot of this morning yesterday my computer run very well ...without problems

---

### Post by coffeecat on 2011-11-14
Yes, I rather expected that.

The next step may be to run testdisk, but hold off for that for the moment. I would really like to see the opinions of the others I've pm'd first and that may take some hours.

---

### Post by Riuzaki90 on 2011-11-14
ok i can wait...what do you mean? is there some odd to repair my disk?

---

### Post by coffeecat on 2011-11-14
Sorry I wasn't clear. You can use Testdisk to restore lost partitions when you have a corrupted partition table, so long as the partition filesystems are still present on the drive. However, testdisk itself can cause problems and is too often recommended before all necessary investigation has been done - that's why I am urging caution.

You can run testdisk from a live Ubuntu CD, but you are using an obsolete version (9.10) and won't be able to download the testdisk package. While we are waiting for others to comment, I suggest you download the ISO for a supported version of Ubuntu - say 10.04 - and burn that to CD. Do you need a link?

---

### Post by Riuzaki90 on 2011-11-14
can I use the 11.10 oneiric ocelot too?

---

### Post by coffeecat on 2011-11-14
> **Riuzaki90 said:**
> can I use the 11.10 oneiric ocelot too?

Yes. If that runs on your machine OK, that will be fine.

---

### Post by Quackers on 2011-11-14
What version of Ubuntu is installed on your system?
When you last used Ubuntu (last night) did you do any partition changing at all?
Please go into your system's bios and check that your hard drive is shown there.

---

### Post by Riuzaki90 on 2011-11-14
I've Ubuntu 11.04 right now...and no i've done no changhes in the partiotion at all...yes my hard drive is shown in my bios correctly...

---

### Post by oldfred on 2011-11-14
I also have never seen a totally erased MBR like this one. At the end of the script it shows gnuparted and size, and just a bit of random data that it took as sda4 near the end of the disk.

I would look at disk with testdisk, just to see if it sees anything useful. But do not write new partition table until posting several screenshots.

You can download testdisk from synaptic, but I do not think 11.10 includes synaptic. Do not know if testdisk is in software center or not.

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

### Post by coffeecat on 2011-11-14
> **oldfred said:**
> You can download testdisk from synaptic, but I do not think 11.10 includes synaptic. Do not know if testdisk is in software center or not.

Good point. I'd forgotten that Synaptic didn't come with 11.10.

@Riuzaki90, testdisk is in the Universe repository which is not enabled by default in the live CD session. If you want to run testdisk in the 11.10 CD, open Ubuntu Software Centre and then from the Software Centre menu, Edit > Software Sources and enable the Universe repository. You then have to refresh the metadata and I don't know how to do that with Software Centre or whether that happens automatically. If you can't find testdisk in Software Centre, close SC and open a terminal, and then:

```
sudo apt-get update
sudo apt-get install testdisk
```

In the 11.04, 10.10 or 10.04 live CDs you can enable the Universe repo in Synaptic and install testdisk with Synaptic too.

Here's another link for running testdisk to add to those oldfred gave you:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

But I agree with oldfred. Don't write anything to the partition table with testdisk just yet. Tell us what it tells you or what it can find.

---

### Post by Riuzaki90 on 2011-11-14
when I was waiting your answer I was installing testdisk from the file that I had downloaded from the site!
I'm here right now...what I've to do?
[IMG]http://img717.imageshack.us/img717/9184/screenshotat20111114171.png[/IMG]
and I see this if I choose Intel and press ANALYSE:
[IMG]http://img843.imageshack.us/img843/9184/screenshotat20111114171.png[/IMG]

---

### Post by coffeecat on 2011-11-14
Choose "intel" which is the mbr partition table type. It's going to be either mbr or GPT, and your laptop is much more likely to be using mbr. There are several stages to go through before you can commit a write, so it's safe to proceed for now and provide screenshots. You are able to go back before writing.

It's the screen after the next after you "analyse" that is going to tell us something.

**EDIT**: you added another screenshot while I was posting. Is that after "analyse"?

---

### Post by Riuzaki90 on 2011-11-14
yes it is after analyse

---

### Post by coffeecat on 2011-11-14
That does not look good. I've only used testdisk a few times, and mostly in simulations. I've not seen it come up with no partitions at all after analyse. Did it offer you a deep search at any point?

---

### Post by Riuzaki90 on 2011-11-14
I'm so sorry, I've post the wrong stampScreen...this is the screenshoot after analyse my disk:
[IMG]http://img689.imageshack.us/img689/4797/screenshotat20111114175.png[/IMG]

it shows correctly my windows7 partition that is about 250 GB....and also the UBUNTU 11.04 that is about 109 GB...how can I restore my files and my systemfiles?

---

### Post by oldfred on 2011-11-14
That looks a lot better. Many times you have several versions of a partition shown with overlap of starts and finishes, so you have to be careful what you want to undelete. Yours looks like all the deleted partitions are unique.  

Do you have backups of data? If data is real valuable you might want to make an image of drive, so any further corruption may be restored for another try. If you have some backups I would just try to  undelete each of these partitions.

---

### Post by Riuzaki90 on 2011-11-14
which ones of the keys I've to change in all the lines?
P?
no I've no backup data file!

---

### Post by coffeecat on 2011-11-14
Sorry for not getting back before. That latest screenshot is more encouraging. It shows 6 partitions but with some gaps between them. The first column under "Start" and "End" is (as far as I can make out) cylinder number -1.

You'll need to decide which were primary and which were logical and mark them accordingly before continuing. Do you know which were primary and logical? Don't forget that you cannot have more than 4 primaries.

I suggest you wait to see if one of the others I've asked to comment does so, but if that was my machine I would proceed on the basis of the information testdisk has thrown up. I'm a bit concerned by those gaps though. Do you remember how many partitions you had originally? Also - the partition labels far right are a bit odd. "SDCARD" is unusual for a hard disk partition label.

If you do go ahead there will still be one definite problem and one likely problem to overcome.

The definite is that the part of the mbr that contains boot code has been overwritten. Even if you restore your partition, you will need to re-install grub to the mbr before you will be able to boot anything. We can help you with that if you need help.

The probable problem is that if testdisk creates an extended partition for the logicals you define, it will more than likely create an illegality in the partition table. It's a known bug, but fortunately fixable. What it will probably do is to define the end sector of the extended partition beyond the physical end of the drive - which is of course impossible. Gparted reacts to this by showing your whole hard drive as "unallocated" as before (another bug), but for a different reason, which will cause you alarm if you are not prepared for this.

This second problem is fixable with an app you can run from the live CD called "fixparts". I can post a link if and when it is needed.

@Quackers and @oldfred, do you agree or have I missed anything?

**EDIT**: it took me so long to type that out - checking testdisk on my own system - that I see oldfred has posted before me!

---

### Post by Riuzaki90 on 2011-11-14
where you can see FAT32 these two lines show a partition that I had for the data...where there's WIN that is the WINDOWS 7 partition and the others are all of ubuntu 11.04 where the last one is the data file partition of ubuntu and the first two I can't image what they are for!

---

### Post by Riuzaki90 on 2011-11-14
can I try to reinstall GRUB and tring to save atleast my ubuntu data?

---

### Post by coffeecat on 2011-11-14
> **Riuzaki90 said:**
> can I try to reinstall GRUB and tring to save atleast my ubuntu data?

You have to restore the partitions first. If you do you can then rescue your data with a live CD before you repair grub, but you cannot reinstall grub before restoring the partition because grub has to point to the Linux root partition where the /boot/grub files are and at the moment you have no partitions to point to. 

If "WIN" is your Windows C: partition, then the first three partitions are almost certainly primary ones, and the last three would then be logical ones.

---

### Post by oldfred on 2011-11-14
I agree with coffeecat. Windows has to be primary, so I would expect the remaining would be logical in an extended. 

Never had to restore partition. It looks like either the left right keys or the L key change partition from D. Some obviously will be primary and some logical which is still a concern. Was one of the partitions swap?

---

### Post by Riuzaki90 on 2011-11-14
yes I think the 400 mega partition with the label LINUX

---

### Post by Riuzaki90 on 2011-11-14
something is gone wrong...I've write the table partition and then I've reboot...now I have this message instead of the boot:

1234F_

what Have I to do?

---

### Post by coffeecat on 2011-11-14
> **Riuzaki90 said:**
> something is gone wrong...I've write the table partition and then I've reboot...now I have this message instead of the boot:

1234F_

what Have I to do?

Have you re-installed grub? If you've only rewritten the partition table, you will still not have a bootloader.

Boot up with the live Ubuntu CD and run the boot script again and also the sfdisk command I posted earlier. Post the output of both and we can see where things are now.

---

### Post by Riuzaki90 on 2011-11-14
now sudo sfdisk -d /dev/sda > Desktop/pt.txtsend this output:

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=   976560, Id=83
/dev/sda2 : start=   978944, size= 13672448, Id=83
/dev/sda3 : start= 30715904, size=488392441, Id= 7
/dev/sda4 : start=519108345, size=457675785, Id= f
/dev/sda5 : start=553369600, size=  8192000, Id= c
/dev/sda6 : start=624316416, size=214843744, Id=83
```

on which one I've to do the grub?

---

### Post by coffeecat on 2011-11-14
> **Riuzaki90 said:**
> now sudo sfdisk -d /dev/sda > Desktop/pt.txtsend this output:

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=   976560, Id=83
/dev/sda2 : start=   978944, size= 13672448, Id=83
/dev/sda3 : start= 30715904, size=488392441, Id= 7
/dev/sda4 : start=519108345, size=457675785, Id= f
/dev/sda5 : start=553369600, size=  8192000, Id= c
/dev/sda6 : start=624316416, size=214843744, Id=83
```

on which one I've to do the grub?

There are three partitions with ext3/4 filesystems so we need the boot script output to be able to tell.

---

### Post by Riuzaki90 on 2011-11-14
ok this is the output:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Testdisk is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 553369600.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:   Syslinux looks at sector 7892 of /dev/sdb1 for its 
                       second stage. According to the info in the boot 
                       sector, sdb1 starts at sector 0. But according to the 
                       info from fdisk, sdb1 starts at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       978,607       976,560  83 Linux
/dev/sda2             978,944    14,651,391    13,672,448  83 Linux
/dev/sda3          30,715,904   519,108,344   488,392,441   7 NTFS / exFAT / HPFS
/dev/sda4         519,108,345   976,784,129   457,675,785   f W95 Extended (LBA)
/dev/sda5         553,369,600   561,561,599     8,192,000   c W95 FAT32 (LBA)
/dev/sda6         624,316,416   839,160,159   214,843,744  83 Linux

/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2062 MB, 2062548992 bytes
64 heads, 62 sectors/track, 1015 cylinders, total 4028416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     4,027,519     4,027,458   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       941fa1b7-274d-41ce-9337-463faa00f20d   ext3       
/dev/sda1        9a642d51-000d-4959-8280-9026c1679224   ext4       
/dev/sda2        96b7acbd-be92-4cd2-ae2b-4d077ba27539   ext4       
/dev/sda3        986C9B406C9B17D8                       ntfs       WIN
/dev/sda5        1C04-1E14                              vfat       SDCARD
/dev/sda6        66a52a18-abd9-4403-86fa-c99cc982b2af   ext4       
/dev/sdb1        C366-1185                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/9a642d51-000d-4959-8280-9026c1679224 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/96b7acbd-be92-4cd2-ae2b-4d077ba27539 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda3        /media/WIN               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/SDCARD            vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


============================= sda1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root 96b7acbd-be92-4cd2-ae2b-4d077ba27539
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 9a642d51-000d-4959-8280-9026c1679224
set locale_dir=($root)/grub/locale
set lang=it_IT
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, con Linux 2.6.38-12-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9a642d51-000d-4959-8280-9026c1679224
    linux    /vmlinuz-2.6.38-12-generic-pae root=UUID=96b7acbd-be92-4cd2-ae2b-4d077ba27539 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-12-generic-pae
}
menuentry 'Ubuntu, con Linux 2.6.38-12-generic-pae (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9a642d51-000d-4959-8280-9026c1679224
    echo    'Loading Linux 2.6.38-12-generic-pae ...'
    linux    /vmlinuz-2.6.38-12-generic-pae root=UUID=96b7acbd-be92-4cd2-ae2b-4d077ba27539 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-12-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, con Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9a642d51-000d-4959-8280-9026c1679224
    linux    /vmlinuz-2.6.38-11-generic-pae root=UUID=96b7acbd-be92-4cd2-ae2b-4d077ba27539 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, con Linux 2.6.38-11-generic-pae (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9a642d51-000d-4959-8280-9026c1679224
    echo    'Loading Linux 2.6.38-11-generic-pae ...'
    linux    /vmlinuz-2.6.38-11-generic-pae root=UUID=96b7acbd-be92-4cd2-ae2b-4d077ba27539 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, con Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9a642d51-000d-4959-8280-9026c1679224
    linux    /vmlinuz-2.6.35-28-generic-pae root=UUID=96b7acbd-be92-4cd2-ae2b-4d077ba27539 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, con Linux 2.6.35-28-generic-pae (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9a642d51-000d-4959-8280-9026c1679224
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /vmlinuz-2.6.35-28-generic-pae root=UUID=96b7acbd-be92-4cd2-ae2b-4d077ba27539 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-28-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9a642d51-000d-4959-8280-9026c1679224
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9a642d51-000d-4959-8280-9026c1679224
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 986C9B406C9B17D8
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/core.img                                  1
               =                grub/grub.cfg                                  1
               =                initrd.img-2.6.35-28-generic-pae               3
               =                initrd.img-2.6.38-11-generic-pae               4
               =                initrd.img-2.6.38-12-generic-pae               1
               =                vmlinuz-2.6.35-28-generic-pae                  2
               =                vmlinuz-2.6.38-11-generic-pae                  3
               =                vmlinuz-2.6.38-12-generic-pae                  2

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=96b7acbd-be92-4cd2-ae2b-4d077ba27539 /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot           ext4    defaults        0       2
/dev/sda5       /home           ext4    defaults,user_xattr        0       2
# swap was on /dev/sda7 during installation
UUID=a5285849-a5df-496c-9399-d8eb82e6b4eb none            swap    sw              0       0
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  eb 58 90 46 52 44 4f 53  34 2e 31 00 02 10 20 00  |.X.FRDOS4.1... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 f9 f6 f0 1e  |........?.......|
00000020  3b 8b 38 01 08 27 00 00  00 00 00 00 12 05 00 00  |;.8..'..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 f2 2c 9e 58 4e  4f 20 4e 41 4d 45 20 20  |..).,.XNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fc fa 29 c0 8e d8  |  FAT32   ..)...|
00000060  bd 00 7c b8 e0 1f 8e c0  89 ee 89 ef b9 00 01 f3  |..|.............|
00000070  a5 ea 7a 7c e0 1f 00 00  60 00 8e d8 8e d0 8d 66  |..z|....`......f|
00000080  e0 fb 88 56 40 be c1 7d  e8 f4 00 66 31 c0 66 89  |...V@..}...f1.f.|
00000090  46 44 8b 46 0e 66 03 46  1c 66 89 46 48 66 89 46  |FD.F.f.F.f.FHf.F|
000000a0  4c 66 8b 46 10 66 f7 6e  24 66 01 46 4c b8 00 02  |Lf.F.f.n$f.FL...|
000000b0  3b 46 0b 74 08 01 c0 ff  06 34 7d eb f3 66 8b 46  |;F.t.....4}..f.F|
000000c0  2c 66 50 e8 94 00 72 4d  c4 5e 76 e8 b7 00 31 ff  |,fP...rM.^v...1.|
000000d0  b9 0b 00 be f1 7d f3 a6  74 15 83 c7 20 83 e7 e0  |.....}..t... ...|
000000e0  3b 7e 0b 75 eb 4a 75 e0  66 58 e8 34 00 eb d2 26  |;~.u.Ju.fX.4...&|
000000f0  ff 75 09 26 ff 75 0f 66  58 29 db 66 50 e8 5a 00  |.u.&.u.fX).fP.Z.|
00000100  72 0d e8 80 00 4a 75 fa  66 58 e8 14 00 eb ec 8a  |r....Ju.fX......|
00000110  5e 40 ff 6e 76 be ee 7d  e8 64 00 30 e4 cd 16 cd  |^@.nv..}.d.0....|
00000120  19 06 57 53 89 c7 c1 e7  02 50 8b 46 0b 48 21 c7  |..WS.....P.F.H!.|
00000130  58 66 c1 e8 07 66 03 46  48 bb 00 20 8e c3 29 db  |Xf...f.FH.. ..).|
00000140  66 3b 46 44 74 07 66 89  46 44 e8 38 00 26 80 65  |f;FDt.f.FD.8.&.e|
00000150  03 0f 26 66 8b 05 5b 5f  07 c3 66 3d f8 ff ff 0f  |..&f..[_..f=....|
00000160  73 15 66 48 66 48 66 0f  b6 56 0d 66 52 66 f7 e2  |s.fHfHf..V.fRf..|
00000170  66 5a 66 03 46 4c c3 f9  c3 31 db b4 0e cd 10 ac  |fZf.FL...1......|
00000180  3c 00 75 f5 c3 52 56 57  66 50 89 e7 6a 00 6a 00  |<.u..RVWfP..j.j.|
00000190  66 50 06 53 6a 01 6a 10  89 e6 8a 56 40 b4 42 cd  |fP.Sj.j....V@.B.|
000001a0  13 89 fc 66 58 73 08 50  30 e4 cd 13 58 eb d9 66  |...fXs.P0...X..f|
000001b0  40 03 5e 0b 73 07 8c c2  80 c6 10 8e c2 5f 00 fe  |@.^.s........_..|
000001c0  ff ff 0c fe ff ff 07 c9  0a 02 00 00 7d 00 00 fe  |............}...|
000001d0  ff ff 05 fe ff ff b0 58  45 06 b7 41 ce 0c 00 00  |.......XE..A....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by coffeecat on 2011-11-14
I'm afraid there are still some inconsistencies, some serious, which will prevent you from booting even if you manage to re-install grub.

First, your /etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=96b7acbd-be92-4cd2-ae2b-4d077ba27539 /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot           ext4    defaults        0       2
/dev/sda5       /home           ext4    defaults,user_xattr        0       2
# swap was on /dev/sda7 during installation
UUID=a5285849-a5df-496c-9399-d8eb82e6b4eb none            swap    sw              0       0
```

Your boot partition (sda1) seems to have been restored. Your root partition was originally sda4, but is now sda2. The UUID checks out, so that should be OK. However, your swap partition (originally sda7) is still missing. Worse, your home partition which was originally sda5 and is probably now sda6 has this in the boot info script output:

```
sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Your system will never boot with a home partition in that state, and it won't boot anyway until you edit /etc/fstab to get the right entry for the home partition. 

Other problems:

The second FAT32 partition with the "NO NAME" label has not been restored.

Lastly, it was as I anticipated - testdisk has put the end sector of the extended partition beyond the physical end of the drive:

```
Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total [COLOR="Red"]976773168[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       978,607       976,560  83 Linux
/dev/sda2             978,944    14,651,391    13,672,448  83 Linux
/dev/sda3          30,715,904   519,108,344   488,392,441   7 NTFS / exFAT / HPFS
/dev/sda4         519,108,345   [COLOR="Red"]976,784,129 [/COLOR]  457,675,785   f W95 Extended (LBA)
/dev/sda5         553,369,600   561,561,599     8,192,000   c W95 FAT32 (LBA)
/dev/sda6         624,316,416   839,160,159   214,843,744  83 Linux

[COLOR="Red"]/dev/sda4 ends after the last sector of /dev/sda[/COLOR]
```

There may be other problems, but I haven't yet found them.

I should think your first priority would be to rescue your data. In theory you can do this from the live CD. **If** the Windows partition filesystem has escaped intact, you should be able to mount that from the live CD and copy your files. The Linux home partition is another matter. You would probably need to run fsck from a terminal to try to repair it before you could rescue any data. Unfortunately, you won't be able to do this from Gparted, because with that partition table irregularity Gparted won't yet recognise any partitions. You can repair that with fixparts but I don't know whether it would be a good idea to do that first, or something else first.

Perhaps the others might like to comment?

---

### Post by Riuzaki90 on 2011-11-14
yes I'll wait also for the other...but may be I'll rescue all my data and format all the disk and remake the two partition!...(windows just for universitary scope [I hate it]) :)

---

### Post by oldfred on 2011-11-14
It looks like you have a separate /boot partition which adds a bit of complication to reinstalling grub2's boot loader. /boot is sda1 and / (root) is sda2.

But testdisk did it usual thing of making the of the extended partition beyond the end of the drive. We need to fix that first. It would be possible to manually update with sfdisk but it is a lot easier to use the program fixparts.

[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Instructions are on the rodsbooks site.

It looks like one partition is missing and you may have some issues with sda6, but those can wait until your run fixparts. Once that works we can reinstall grub2's boot loader to the MBR.

---

