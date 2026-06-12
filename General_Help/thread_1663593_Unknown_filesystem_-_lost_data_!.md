---
title: "Unknown filesystem - lost data !"
date: 2011-01-09
forum: General Help
---

### Post by Alpine725 on 2011-01-09
I am having an issue with my Toshiba laptop.  After the Toshiba splash screen, all I see is:
error: unknown filesystem
grub rescue>

Ubuntu 10.04 is the only thing installed and I didnt back up the sentimental data before things went south.

My original call for help can be found here:

[http://ubuntuforums.org/showpost.php?p=10299431&postcount=127](http://ubuntuforums.org/showpost.php?p=10299431&postcount=127)

To read the subsequent posts click the "Megathread" link in the upper right of the window.

Here are of the contents of my RESULTS.txt file:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   149,843,967   149,841,920  83 Linux
/dev/sda2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sda5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2: PTTYPE="dos" 
/dev/sda5        aab6abfc-55df-4598-bc9c-62a6410e6249   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  d2 bc 14 00 e2 bc 14 00  f2 bc 14 00 02 bd 14 00  |................|
00000010  a0 04 62 00 22 bd 14 00  e0 57 aa 00 80 0d a8 00  |..b."....W......|
00000020  52 bd 14 00 62 bd 14 00  72 bd 14 00 82 bd 14 00  |R...b...r.......|
00000030  92 bd 14 00 a2 bd 14 00  b2 bd 14 00 c2 bd 14 00  |................|
00000040  d2 bd 14 00 e2 bd 14 00  f2 bd 14 00 02 be 14 00  |................|
00000050  50 c7 a3 00 30 12 a8 00  32 be 14 00 42 be 14 00  |P...0...2...B...|
00000060  52 be 14 00 62 be 14 00  72 be 14 00 82 be 14 00  |R...b...r.......|
00000070  92 be 14 00 20 2b a8 00  b2 be 14 00 c2 be 14 00  |.... +..........|
00000080  d2 be 14 00 e2 be 14 00  40 fc 61 00 02 bf 14 00  |........@.a.....|
00000090  12 bf 14 00 22 bf 14 00  32 bf 14 00 42 bf 14 00  |...."...2...B...|
000000a0  52 bf 14 00 62 bf 14 00  72 bf 14 00 82 bf 14 00  |R...b...r.......|
000000b0  92 bf 14 00 a2 bf 14 00  b2 bf 14 00 c2 bf 14 00  |................|
000000c0  d2 bf 14 00 e2 bf 14 00  f2 bf 14 00 02 c0 14 00  |................|
000000d0  12 c0 14 00 22 c0 14 00  32 c0 14 00 10 30 a8 00  |...."...2....0..|
000000e0  52 c0 14 00 62 c0 14 00  72 c0 14 00 82 c0 14 00  |R...b...r.......|
000000f0  92 c0 14 00 a2 c0 14 00  b2 c0 14 00 c2 c0 14 00  |................|
00000100  d2 c0 14 00 30 58 aa 00  f2 c0 14 00 02 c1 14 00  |....0X..........|
00000110  12 c1 14 00 c0 fc 61 00  32 c1 14 00 a0 63 a9 00  |......a.2....c..|
00000120  52 c1 14 00 62 c1 14 00  72 c1 14 00 82 c1 14 00  |R...b...r.......|
00000130  92 c1 14 00 a2 c1 14 00  20 cc ac 00 c2 c1 14 00  |........ .......|
00000140  d2 c1 14 00 e2 c1 14 00  f2 c1 14 00 02 c2 14 00  |................|
00000150  12 c2 14 00 22 c2 14 00  20 9b ac 00 42 c2 14 00  |...."... ...B...|
00000160  20 26 a8 00 62 c2 14 00  72 c2 14 00 82 c2 14 00  | &..b...r.......|
00000170  92 c2 14 00 a2 c2 14 00  b2 c2 14 00 c2 c2 14 00  |................|
00000180  d2 c2 14 00 e2 c2 14 00  00 0a a8 00 02 c3 14 00  |................|
00000190  12 c3 14 00 22 c3 14 00  32 c3 14 00 42 c3 14 00  |...."...2...B...|
000001a0  a0 51 24 00 00 00 00 00  01 00 00 00 60 d7 a7 00  |.Q$.........`...|
000001b0  40 d8 a7 00 80 e7 a7 00  60 d7 a7 00 40 d8 00 fe  |@.......`...@...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 80 62 00 00 00  |............b...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

I finally managed to boot from the LiveCD.  I dont so much mind as much if I cant get the 10.04 install running as much as I really want to get my data back.  The bulk of the data was on the desktop and in the downloads directory.

Is there anyone out there that can help me out?  :confused:
Thanks in advance.

---

### Post by VonFilmjölk on 2011-01-09
lets see here, when u boot from live CD u can find you personal data in the download folder right, that means that u can find the filesystem. from my experience there should be no loss of information. when I had a similar issue i just needed to reinstall the grub,  have u tried reinstalling the grub? 
 here is a easy walkthrough  [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Alpine725 on 2011-01-10
> **VonFilmjölk said:**
> when u boot from live CD u can find you personal data in the download folder right

I cant say yes or no.  All I can say is that I have been unable to locate my "stuff".  It could be that I am not looking in the right place.  When I said my data is on the Desktop and in the Downloads folder, I meant the ubuntu install than I am having trouble getting to.

I have tried Gparted and it errors out and fails to start.  I saw something called TestDisk...can anyone tell me if that will help me get my data back?

Thanks in advance.

---

### Post by VonFilmjölk on 2011-01-10
ok ill write down a quick guide, to make sure we are on the right page.


first boot from your liveCD choose the option "try Ubuntu" then when Ubuntu has started  press "places" in the panel (in the top left of the screen) under computer you should see the cd-drive/penndrive and under that the different partitions, if u press computer  should see a Icon named filesystem, and since you are now booting from a live cd you should have another icon that looks the same (dont know what the name of it will be on your computer) , if u open both of these  and they have have same folders,  IE bin, boot cdrom, and so on. Then your "stuff" is still there.

and if u haven't tried reinstalling the grub try it. cause a faulty grub is most likely the cause, 

if the case is that u don't know your way around the terminal, or don't understand what to do with the guide i linked earlier. just ask and I'll help.

---

### Post by Alpine725 on 2011-01-11
First of all, sorry for the delay in responding, I was working all day and am only getting back to this now.

> **VonFilmjölk said:**
>  under computer you should see the cd-drive/penndrive and under that the different partitions, if u press computer  should see a Icon named filesystem, and since you are now booting from a live cd you should have another icon that looks the same (dont know what the name of it will be on your computer) , if u open both of these  and they have have same folders,  IE bin, boot cdrom, and so on. Then your "stuff" is still there.


So...if I understand correctly after I open 'Computer' from the 'Places' menu, I should see 2 'Filesystem' icons?  If when ubuntu gets installed it gives your hard drive a name then thats what it would be called, however, there is only one 'Filesystem' icon and when I open it and start rummaging through the folders, it looks like I may be looking at the LiveCD filesystem.

I havent tried replacing Grub yet because I dont really want to write anything to the drive in fear of over writing some of my stuff.

I am going to look into TestDisk and see if that might help.

Any other suggestions?
Thanks again!!

---

### Post by Quackers on 2011-01-11
Do you recall what happened that could have caused sda1 to become unmountable? Did you run updates or was the power cut or anything like that?

---

### Post by Alpine725 on 2011-01-11
> **Quackers said:**
> Do you recall what happened that could have caused sda1 to become unmountable? Did you run updates or was the power cut or anything like that?

I fired up my Toshiba Satellite A105 laptop (on which ubuntu 10.04 has been the only OS - no other partitions - since its release) the morning of Dec 29th, for the first time in a week (was away for Christmas). After firing it up, needing a charge, I plugged in my iPod Touch. I dont think it would have affected the startup since ubuntu typically starts to usable in about 45 seconds to a minute and I plugged in the iPod after a couple minutes - at least I thought it was. I didnt sit right down so I dont know if there was anything odd on the screen during boot up or once it got into ubuntu after I plugged in the iPod.  When I did finally sit down to use the laptop, I had the "task bar" at the top with a blank desktop (not the picture I left when I shut it down a week ago) and several notification boxes that instead of english text, they all had squares where the text would be (like it was a foreign language for which I didnt have the proper language pack installed) and at the bottom of each, it said something about something being prevented from running. I had the option of 'delete' and 'dont delete'. Thinking back to my windows boxes, I saw the squares for text and though "malware" and proceeded to click on 'delete'. After that, the only thing that worked was the mouse pointer. I shut down (by holding the power button) and rebooted and here I am.

---

### Post by Quackers on 2011-01-11
On booting are you getting the grub menu up? If not hold down the shift key. There is likely to be a recovery option in the grub menu, try that.

Edit, in retrospect that is unlikely to work. It may be that testdisk run from the live cd may be your best option to recover the partition, or photorec (I think it's called) to recover data.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by Alpine725 on 2011-01-12
So, I was looking into the TestDisk program...I see there are several different versions.  Assuming I want to get the ubuntu rescue remix, what version should I get?  I am using the 10.10 LiveCD but the install I am trying to access is 10.04.  Should I use the 10.04 ubuntu rescue remix or the 10.10 version?

Also, I see there is a GUI version...not wanting to copy anything to the drive in fear of writing over any of my stuff, should I grab a different version - maybe the knoppix option?

Anyone have any insights on the matter?

If there is anyone out there that thinks TestDisk wont help me rectify my boot issues, please let me know...I am still open to suggestions.

Thanks again to all...

---

### Post by matt_symes on 2011-01-12
Hi

Have you tried to fsck the partition from the LiveCD?

It might be a corrupted superblock and you might be able to fix that.

Kind regards

---

### Post by Alpine725 on 2011-01-12
Either I am so far removed from command line interfaces or I am doing something wrong because when I type 'fsck' from the 'ubuntu@ubuntu:/$' prompt, all I get is:

fsck from util-linux-ng 2.17.2

Where did I go wrong?

---

### Post by VonFilmjölk on 2011-01-12
Just so you know reinstalling the grub will not affect our data.
 
with that said, I have no clue what might have caused you problems since the series of events that followed by you connecting your ipod are new to me and this conversation. although i still think the grub might be the villain.
 I now leave you in the hands of the elderly members of this forum,  they are more experienced than me and I do not wish to be a source of confusion.

Vonfilmjölk

---

### Post by Alpine725 on 2011-01-12
OK...So I managed to get into TestDisk.  I think it "sees" the partitions, however, when I try to 'list files' by pressing 'p', I see:

Directory/

No file found, filesystem seems damaged.

Now what...  :-/

---

### Post by matt_symes on 2011-01-12
Hi

I will explain what i mean by fsck.

From the LiveCD open a terminal and type

```
sudo dumpe2fs /dev/sda1 | grep -i backup
```

If all goes well with that you will get an output like

```
journal backup:           inode blocks
  Backup superblock at **32768**, Group descriptors at 32769-32771
  Backup superblock at 98304, Group descriptors at 98305-98307
  Backup superblock at 163840, Group descriptors at 163841-163843
  Backup superblock at 229376, Group descriptors at 229377-229379
```

This is a list of the backup superblocks.

You can then run

```
sudo fsck -y -b **32768** /dev/sda1
```

Changing the bold 32768 above to the bold value returned in dumpe2fs. Hopefully that might get you somewhere.

Kind regards

---

