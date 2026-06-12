---
title: "Can I create a partition on my windows xp and then install ubuntu to that partition"
date: 2011-03-17
forum: General Help
---

### Post by adamf4i on 2011-03-17
then have a dual boot option to pick wether to load xp or ubuntu ,

I want to make sure I can install ubuntu and  get it working correctly IE loaded all drivers and install a media sharing device to view on my xbox 360 and install firefox and utorrent , This is basically just a media machine to do everything on my xbox 360. 

I dont want to install it from scratch in case there is a problem then I just set myself up for a bunch of work to get it running correctly again

Any help is appreciate

---

### Post by coffeecat on 2011-03-17
**EDIT**: Oops sorry!. I misread your post to say that you wanted to use Windows to create the Ubuntu partition. :oops: Even though it doesn't answer your question, I'll leave what I posted below because it is valid.

Yes, you can create partitions on a Windows machine to install Ubuntu to. The link below is useful.

Original post:

[COLOR=SlateGray]The windows XP installer creates partitions with the Microsoft NTFS filesystem. Although Ubuntu can read and write to NTFS, it is not suitable for installing a Linux system to.

Although the Windows XP installer recognises extended and logical partitions, it (as far as I can tell) only creates primary partitions. Since Linux can boot from logical partitions you might prefer to create logical partitions for Ubuntu. If nothing else, that gives you more flexibility because you can exceed the 4 primary partition limit that way.[/COLOR] [COLOR=SlateGray]

You need at least two partitions for Ubuntu - a root partition and a swap partition. Some people prefer a separate /home partition, and/or a data partition to be shared between Ubuntu and Windows is very useful. All of this requires a more sophisticated partitioner than the Windows XP has.[/COLOR] 

Decide on your needs and then use Gparted from the live CD. You might find this link useful:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by adamf4i on 2011-03-17
Can you walk me through doin something like this I have aim,and msn messengers on my phone so I can chat through there , If I can get this OS installed I wouldnt care about having windows xp at all just want to make sure I can get all the drivers installed and be able to stream some stuff to my xbox 

Basically need some walkthrough to install ubuntu . ALso on this isntall can I download to usb drive? to install?

Like I said I would like to do away with windows completly just want to make sure I can get all the drivers installed and the ushare program to be able to stream everything to my xbox

I was thinking I could create a partition install ubuntu on it then once I get it all working I would move over some music/video files and delete all the windows xp and just add that partition space back to my whole area

---

### Post by lithopsian on 2011-03-17
Download ISO file, burn to CD, insert CD, boot, follow instructions.

If you can't burn a CD you can buy one for basically the cost of the postage.

You can also copy the ISO to some other bootable device such as a USB driver and install from there.

It is also possible to install over a network.

You might also want to search Wubi, not that I recommended that you understand ;)

---

### Post by mastablasta on 2011-03-17
> **adamf4i said:**
>  
Basically need some walkthrough to install ubuntu . ALso on this isntall can I download to usb drive? to install?
 
 
read the manual.
 
before making disk partition and disk resizing you will need to do defragmentation of the disk and also checkign the disk with chkdsk. probably at least 2 times. second defrag is quite fas, bt first one might take a while.
 
yes you can make a bootable USB. use unebootin or linux live USb creator (very nice interface with all checkups)
 
 
 [QUOTE]
I was thinking I could create a partition install ubuntu on it then once I get it all working I would move over some music/video files and delete all the windows xp and just add that partition space back to my whole area [QUOTE]
 
the adding of parittion might not work as planned.:( but you can also just keep it. Linux can read NTFS. but it's better to have ext3 or ext4 for the systems partition.
 
I suggest you create a bootable USB drive (if your computer can boot from USB and because it will be faster to test it). You can then try installing the drivers and such (most drivers are part of linux kernel except for a few proprietary ones). in this Live session everything is loaded to RAM so when you restart/turn off computer all changes are lost. but you can still try drivers and see if your xbox can be mounted.
 
problematic hardware is:
 
SIS onboard graphics cards
certain mobile Radeon chips
some new Nvidia mobile chips and maybe some really old ones
some newer sound ships (Intel HD audio, realtek)
cetain wi-fi cards/chips
TV tunners
 
the rest should work.
 
oh and some motherboards can't suspend/hibernate propperly.

---

### Post by pqwoerituytrueiwoq on 2011-03-17
> **coffeecat said:**
> [COLOR=SlateGray]4 primary partition limit that way.[/COLOR] 
My 32bit XP pro sp3 cd thinks it is 3 (stupid windows)
which can be a real pain if you are installed xp second

---

### Post by oldfred on 2011-03-17
Examples of installs with screen shots:

Installs -----------------------
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by coffeecat on 2011-03-17
> **pqwoerituytrueiwoq said:**
> My 32bit XP pro sp3 cd thinks it is 3 (stupid windows)
which can be a real pain if you are installed xp second

The Windows installer gets horribly confused by logical partitions with Linux filesystems on them, so beware when installing XP when Linux is already present. There have been several threads concerning corrupted partition tables because of this - corrupted by the Windows installer. Also, don't forget that you can only have three primary partitions if you have an extended partition, because an extended partition is simply a special type of primary which is used only as a placeholder for logical partitions.

---

