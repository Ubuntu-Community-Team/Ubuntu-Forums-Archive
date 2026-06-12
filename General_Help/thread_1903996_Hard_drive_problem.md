---
title: "Hard drive problem"
date: 2012-01-03
forum: General Help
---

### Post by dRounse on 2012-01-03
I am building a server abd i got a new 2TB seagate harddrive the green eco friendly one and i cannot for the life of me get any operating system i install to boot, i have tried, Lubuntu, Xubuntu, Ubuntu, openSUSE, and debain, if someone could tell me what im doing wrong it would be much appreciated... when i turn the computer on it says there is nothing to boot.

---

### Post by perrti-y02 on 2012-01-03
Are they recognised by the BIOS? That might, at least, give you more information.

---

### Post by |{urse on 2012-01-03
Go into the bios and make sure your hard-disk isn't set to RAID, if it is set it to SATA, AHCI, IDE or whatever else you have as an option. Also try plugging your sata cable into a different sata port.

Try using a bootcd instead. Just to see if it works.
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) <-- download the iso, boot to disk, try to boot unbootable os on hard drive.

If the bootcd worked then a low-level format might help you out.

[http://www.dban.org/](http://www.dban.org/) <-- download the iso, burn to disk and nuke that sucker.

Could also be that you have bad sector(s). 

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd) <-- download the iso, burn to disk and select HDD Regenerator, let it run completely then try to use your drive again.

Theres a bunch of other things it could be and a bunch of different ways to do what I've suggested so keep an eye out for suggestions :)

---

### Post by dRounse on 2012-01-03
> **perrti-y02 said:**
> Are they recognised by the BIOS? That might, at least, give you more information.

It knows its plugged in but i think, because ofsome research that its due to thae fact that it is over 137gb which is a little confusing, also i am nuking the hard drive right now

---

### Post by topsites on 2012-01-04
If you're speaking of "nuking" a hard drive I am not sure you should be fooling with it.

---

### Post by dRounse on 2012-01-04
> **topsites said:**
> If you're speaking of "nuking" a hard drive I am not sure you should be fooling with it.

The person above me said to use DBAN so i used that is that ok? I can stop it if thats bad but the hard drive is being picked up and i can install an OS but i cant boot the OS thats the problem

---

### Post by HermanAB on 2012-01-04
Well, dban isn't going to help, so you can stop that waste of time.

---

### Post by mastablasta on 2012-01-04
Actually low level format is suggested by disk manufacturers in these cases. i know this because i had same/simila thing with WD green. I think these greeen drives are actually not ment to put the system on at least the big ones. Plenty people having issue with them. again sometimes they do work as they should... i haven't found any issue on my HD. even their disk diagnostic utility didn't show any errors. yet certain data keep getting "corrupted" preventing system to boot. will do some more testing with real data (not OS), if nothing happens, good. Else i will return it/exchange it.

---

### Post by dRounse on 2012-01-04
> **mastablasta said:**
> Actually low level format is suggested by disk manufacturers in these cases. i know this because i had same/simila thing with WD green. I think these greeen drives are actually not ment to put the system on at least the big ones. Plenty people having issue with them. again sometimes they do work as they should... i haven't found any issue on my HD. even their disk diagnostic utility didn't show any errors. yet certain data keep getting "corrupted" preventing system to boot. will do some more testing with real data (not OS), if nothing happens, good. Else i will return it/exchange it.

What would be a good low level formatting program? And i also had the WD green but i exchanged it for this because i thought it was a broken, but clearly they just dont want an os on them, could i use my 120 gb hard drive as the main os and connect this 2 tb hard drive for more space in the server?

---

### Post by ottosykora on 2012-01-04
>because ofsome research that its due to thae fact that it is over 137gb which is a little confusing,<

if there is in whole process somewhere a note that there is some 137 incompatibilty, then it is a fact and it is a bios problem and can not be cured unless there is new bios av.

Nuking does not help in such case and it does not help in any other case where the drive is not recognized. It is just to wipe all from the drive.
There will be many, many computers today which will not be able to deal with 2T drives at all. I have only one computer which is able to deal with it, it is a rather new HP notebook, but all others, older then some 4 years, can not deal with it at all.

---

### Post by ottosykora on 2012-01-04
>What would be a good low level formatting program? <

I don't know what others mean by low level format, but for me such thing was possible some 20 years ago, when controller circuits allowed low level format the real disk in fact. The biggest low level format disk I ever manged was 500mb (yes mb, not gb!) 
The low level format was mainly done by calling up a program for that via bios and this was in general stored in the controller.

There is nothing generic for that today, when we talk about things like nuke, this is not low level format, it is just common wipe of the preformated storage space on the disk. 
It is working via the controller firmware, so it will not do anything to the spare sectors space etc.

Due to large spare areas on the drives today, low level format would definitely destroy the whole disk completely, as the spare areas would then not be properly included and would therefore be probably lost.

---

### Post by dRounse on 2012-01-04
> **ottosykora said:**
> >because ofsome research that its due to thae fact that it is over 137gb which is a little confusing,<

if there is in whole process somewhere a note that there is some 137 incompatibilty, then it is a fact and it is a bios problem and can not be cured unless there is new bios av.

Nuking does not help in such case and it does not help in any other case where the drive is not recognized. It is just to wipe all from the drive.
There will be many, many computers today which will not be able to deal with 2T drives at all. I have only one computer which is able to deal with it, it is a rather new HP notebook, but all others, older then some 4 years, can not deal with it at all.

Should i return it and get a couple smaller hard drives? Or can it not handle 2 tb in any way?

---

### Post by |{urse on 2012-01-04
> **HermanAB said:**
> Well, dban isn't going to help, so you can stop that waste of time.

Sorry, but you're wrong, low-level format is the smartest next step to try here. After the bios and physical connections to and from the drive are ruled out as issues, of course.

---

### Post by |{urse on 2012-01-04
> There is nothing generic for that today, when we talk about things like nuke, this is not low level format, it is just common wipe of the preformated storage space on the disk. 
It is working via the controller firmware, so it will not do anything to the spare sectors space etc.

Nope, by "nuke" with dban I meant a real low-level format. :confused:

---

### Post by dRounse on 2012-01-04
The computer is detecting it, it wont boot, i can install an OS. I dont know if it cant handle, but i found a program on that boot cd and it let me set up a 137 gb windows xp partition and i was thinking could i just us gparted after and use the whole 2 tb hard drive, then install linux?

---

### Post by spacecheck on 2012-01-04
In order to create such large disks, they have to use a different sector size (4kb instead of 512b). Since some operating systems are unable to recognize and  properly handle the different size, the manufacturers will often include a software to translate the sector size for the OS, making the OS think it is using the standard sector size.
 There will often be a notice about this on the device, or included in the package, or at the mfg website.
Linux is supposed to be capable of recognizing the drives and properly assigning sectors, but there may have been an incorrect partitioning by/for WinXp which did not map (align the partition) to the correct sector sizes.

---

### Post by dRounse on 2012-01-04
> **spacecheck said:**
> In order to create such large disks, they have to use a different sector size (4kb instead of 512b). Since some operating systems are unable to recognize and  properly handle the different size, the manufacturers will often include a software to translate the sector size for the OS, making the OS think it is using the standard sector size.
 There will often be a notice about this on the device, or included in the package, or at the mfg website.
Linux is supposed to be capable of recognizing the drives and properly assigning sector
s, but there may have been an incorrect partitioning by/for WinXp which did not map (align the partition) to the correct sector sizes.

So what would i need to do to install Ubuntu and have it boot properly?

---

### Post by topsites on 2012-01-04
Lets try another route.

Is this your hard-drive:
[http://www.seagate.com/ww/v/index.jsp?name=st32000542as-bcuda-lp-sata-2tb-hd&vgnextoid=1f70e5daa90b0210VgnVCM1000001a48090aRCRD&locale=en-US](http://www.seagate.com/ww/v/index.jsp?name=st32000542as-bcuda-lp-sata-2tb-hd&vgnextoid=1f70e5daa90b0210VgnVCM1000001a48090aRCRD&locale=en-US)

If not, please try and pull your hard-drive out of your system and list us here all of the model / serial numbers and specifications of any and all manufacturer's labels... So that perhaps we can access some support via Seagate this way.

Here is some BS:
[http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=196169&Hilite=](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=196169&Hilite=)

---

### Post by dRounse on 2012-01-04
> **topsites said:**
> Lets try another route.

Is this your hard-drive:
[http://www.seagate.com/ww/v/index.jsp?name=st32000542as-bcuda-lp-sata-2tb-hd&vgnextoid=1f70e5daa90b0210VgnVCM1000001a48090aRCRD&locale=en-US](http://www.seagate.com/ww/v/index.jsp?name=st32000542as-bcuda-lp-sata-2tb-hd&vgnextoid=1f70e5daa90b0210VgnVCM1000001a48090aRCRD&locale=en-US)

If not, please try and pull your hard-drive out of your system and list us here all of the model / serial numbers and specifications of any and all manufacturer's labels... So that perhaps we can access some support via Seagate this way.

Here is some BS:
[http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=196169&Hilite=](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=196169&Hilite=)

Yes that first link is the drive, i just checked.

---

### Post by spacecheck on 2012-01-05
> **dRounse said:**
> So what would i need to do to install Ubuntu and have it boot properly?

Perhaps you should review these:

Sector size and installation considerations:
[http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=221411&NewLang=en&Hilite=sector+size](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=221411&NewLang=en&Hilite=sector+size)

Formatting:
[http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=203931&NewLang=en](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=203931&NewLang=en)

With these in mind, perhaps the prior partitioning (for your WinXp installation) was not done with consideration for sector size and alignment. Perhaps your choice would be to create a new partition table (losing all data from the drive), possibly using their tool's "Erase track zero" format function.

I also recall reading (in the  man page for fdisk) "fdisk  does  not  understand GUID partition tables (GPTs) and it is not designed for large partitions.  In these cases, use the  more  advanced GNU parted ( 8 )." 

In the same man page, there is a warning about dos 6.1 error, which goes on to suggest running "the command "dd if=/dev/zero of=/dev/sda1 bs=512 count=1"  to zero the first 512 bytes of the partition.", but this probably would not apply to a disk with 4kb sectors.

If your main board BIOS accepts/recognizes GPT partition tables, you should be able to delete the old (GPT or msdos MBR) partition table using gparted and then create a new GPT (I'm not sure if you need to reboot afterwards, for it to be recognized properly, but it couldn't hurt). Then, you could add  a few new partitions (at least /, /home, and /swap) and format them for Linux. The Livecd system should immediately be able to recognize and install to the new partitions.

Good luck!

---

### Post by dRounse on 2012-01-05
> **spacecheck said:**
> Perhaps you should review these:

Sector size and installation considerations:
[http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=221411&NewLang=en&Hilite=sector+size](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=221411&NewLang=en&Hilite=sector+size)

It says the linux kernel now supports 4kb sectors.

> With these in mind, perhaps the prior partitioning (for your WinXp installation)

I havent installed WinXP yet, i was going to but there is currently no OS

>  I also recall reading (in the  man page for fdisk) "fdisk  does  not  understand GUID partition tables (GPTs) and it is not designed for large partitions.  In these cases, use the  more  advanced GNU parted ( 8 )."

If your main board BIOS accepts/recognizes GPT partition tables, you should be able to delete the old (GPT or msdos MBR) partition table using gparted and then create a new GPT (I'm not sure if you need to reboot afterwards, for it to be recognized properly, but it couldn't hurt). Then, you could add  a few new partitions (at least /, /home, and /swap) and format them for Linux. The Livecd system should immediately be able to recognize and install to the new partitions.

So once i boot up gparted what should i do? Im never good doing my own partitions:-(

---

### Post by spacecheck on 2012-01-05
If you boot a livecd and start gparted, it should see your hdd, if installed properly. 

Installed properly means you set the BIOS settings to enable the onboard (or added, yet properly-addressed) SATA controller. Then you made sure the port you want to use for it is also turned on (look at the plug, or its picture in the handbook, to determine which port it is). Then you select the type of access you want it to have (DMA,, highest possible SATA throughput, SATAIII for that HDD, SATAII or even less, if the controller is older).

Then you would reboot into the BIOS again to ensure the device is visible with all its bells and whistles enabled and, if so, you'd set the device boot priority so it will start first, if there is an OS on it.

All that done, you'd crank up the livecd, and select language, then F3 for the desired keyboard selection then hit enter for "Try Ubuntu before installing..."

When it comes on line, you'd call up gparted and see if there is a visible device with (new) no partitions. Once there, you would select, "Create Partition" and tell it which kind you want. A newer mainboard (check the manual) will accept GUID Partition Tables (GPT) and you could select that, which would create a GPT partition table, but no partitions.

I'm not sure you need a reboot here, but it would waste only a little time. Then you could decide to set a variety of diverse partition options, which vary with intent and purpose of the server.

You will want at least one partition for /  and one for /swap and possibly a variety of others, maybe even a large one for user space /home if users will be allowed access for their own files.

But, that is something you will have to design after you get a functional partition table. See how far this helps and let us know how it goes.

Good luck!

---

### Post by imachavel on 2012-01-05
that was so thorough, I think I can't handle it :popcorn:

I just usually see if the bios sees the ram(pc won't start without it) sees the cd rom drive and hdd. Then I pop in gparted then partition it off. If I was as thorough as you, I'd be at the top of the chain. Way to explain it in vast detail ;)

to OP, when using gparted, make sure that the file system matches up with what you want installed. e.g. windows select to partition off the drive with ntfs, linux ubuntu natty narwhal partition off the drive with ext2 or ext3 or ext4 file system. I'm sure previous replier will be much more suitable to explain which type of file system is best with your hdd, and your processor speed, psu, mobo etc. Jesus I'm bad

and yes don't forget swap

---

### Post by dRounse on 2012-01-05
> **spacecheck said:**
> If you boot a livecd and start gparted, it should see your hdd, if installed properly. 

Installed properly means you set the BIOS settings to enable the onboard (or added, yet properly-addressed) SATA controller. Then you made sure the port you want to use for it is also turned on (look at the plug, or its picture in the handbook, to determine which port it is). Then you select the type of access you want it to have (DMA,, highest possible SATA throughput, SATAIII for that HDD, SATAII or even less, if the controller is older).

Then you would reboot into the BIOS again to ensure the device is visible with all its bells and whistles enabled and, if so, you'd set the device boot priority so it will start first, if there is an OS on it.

All that done, you'd crank up the livecd, and select language, then F3 for the desired keyboard selection then hit enter for "Try Ubuntu before installing..."

When it comes on line, you'd call up gparted and see if there is a visible device with (new) no partitions. Once there, you would select, "Create Partition" and tell it which kind you want. A newer mainboard (check the manual) will accept GUID Partition Tables (GPT) and you could select that, which would create a GPT partition table, but no partitions.

I'm not sure you need a reboot here, but it would waste only a little time. Then you could decide to set a variety of diverse partition options, which vary with intent and purpose of the server.

You will want at least one partition for /  and one for /swap and possibly a variety of others, maybe even a large one for user space /home if users will be allowed access for their own files.

But, that is something you will have to design after you get a functional partition table. See how far this helps and let us know how it goes.

Good luck!

Let me see if i did this already... i started the actual gparted cd and gparted popped up and i clicked create partition table, which by default uses msdos,so i changed it to gpt and then re booted with a debian cd and installed, i did the auto partitionand had the /home on a seperate partition and it installed the OS but it wont boot

---

### Post by imachavel on 2012-01-05
did you partition it with swap? did you partition it to the exact type of file system as the OS that you want installed? What else is on the hdd? pop it in there, try and remove and then re create the partition. don't shrink it or expand it might screw up how the drive writes and reads it, at which point the drive won't think that the partition is contiguous

Otherwise who knows what went wrong. Did you try everything that space check said? well, hope it works out somehow. make sure you add in swap space. How large of a partition did you create how many gb? I think think most OS need at least 5gb to just basically install, it not much more + swap space

---

### Post by spacecheck on 2012-01-05
In gparted, you also have to set the label for the boot partition to "boot."

---

### Post by dRounse on 2012-01-05
There was a 4.1 gb swap which was auto set when i installed debian, and it had the boot flag there already

---

### Post by spacecheck on 2012-01-05
Well, there aren't any files in /swap that are interested in booting anything, so you'll prob'ly want to set the "boot" flag on the partition containing the /boot files.

Hopefully Grub was installed in the correct spot, too.

---

### Post by dRounse on 2012-01-05
> **spacecheck said:**
> Well, there aren't any files in /swap that are interested in booting anything, so you'll prob'ly want to set the "boot" flag on the partition containing the /boot files.

Hopefully Grub was installed in the correct spot, too.

I meant there is a boot flag on the other partions, and its not just debian its every os i install idont think grub is messed up on all of them

---

### Post by spacecheck on 2012-01-05
> not just debian its every os i install
How many OSs did you install??

---

### Post by dRounse on 2012-01-05
> **spacecheck said:**
> How many OSs did you install??

Only one at a time, i have tried ubuntu, lubuntu, debian, and opensuse but i have made sure they were wiped before i tried with a diff operating system

---

### Post by dRounse on 2012-01-05
What if i just combined the hard drive with a 128 gb, and use thesmaller one as the main one with the OS and the larger one as the storage for the server

---

### Post by larrypg on 2012-01-05
Hello,

I read the first few entries but then got lost a bit...you have a 2 TB drive.  Some systems see this as a gpt (sp?) disk and use uefi to boot.  Sorry if my terminolgy is wrong but it might be the problem. 

I have a 2 TB hd and cut it down so that Ubuntu takes (including home files) 500 Gib.  This put it witin the normal booting of MBR (MSDOS) range.  

Sorry if this was already mentioned but just thought I would throw it out.

---

### Post by spacecheck on 2012-01-06
> **dRounse said:**
> What if i just combined the hard drive with a 128 gb, and use the smaller one as the main one with the OS and the larger one as the storage for the server

You also wrote:
> I am building a server
So your needs will be determined by what type of server you are intending build and what kind of performance will be required from it. The number of users, access requests, data security (RAID? Backups?), whether or not it is a web server, application server, database server, home/family server, and etc., etc., etc., are all considerations to keep in view.

If you have an extra 128GB HDD sitting in the corner looking bored and lonely and have a free HDD-slot, an extra cable, plus enough power in the PSU and are willing to pay the extra watt hours it will use if installed (and to keep it cool), then there isn't any reason why not to add it to the box.

If so, you would surely want to do a minor bit of load balancing, simply by putting the /swap on the one HDD and the OS on the other. Unless you're installing so much RAM that using a /SWAP would be silly.

You could still assign the most demanding requirements to the one (faster) drive and the others to the slower one.

Decisions, decisions, decisions, so many alternatives from which to choose.

Have fun!

---

### Post by dRounse on 2012-01-06
> **spacecheck said:**
> You also wrote:

So your needs will be determined by what type of server you are intending build and what kind of performance will be required from it. The number of users, access requests, data security (RAID? Backups?), whether or not it is a web server, application server, database server, home/family server, and etc., etc., etc., are all considerations to keep in view.

If you have an extra 128GB HDD sitting in the corner looking bored and lonely and have a free HDD-slot, an extra cable, plus enough power in the PSU and are willing to pay the extra watt hours it will use if installed (and to keep it cool), then there isn't any reason why not to add it to the box.

If so, you would surely want to do a minor bit of load balancing, simply by putting the /swap on the one HDD and the OS on the other. Unless you're installing so much RAM that using a /SWAP would be silly.

You could still assign the most demanding requirements to the one (faster) drive and the others to the slower one.

Decisions, decisions, decisions, so many alternatives from which to choose.

Have fun!

I want it to be a family and file server, i want to be able to access my stuff other places than my house and stream it also.... i have a 120 gb hard drive that i can install the OS on and it will mount the 2 tb hard drive, because no OS will boot off the 2 tb. I have 2 gb of RAM, im not sure if a swap file is necessary but inthe few years ive used linux  2 gb has been enough, i plan on using debian with xfce, or would ubuntu wotk better? I know a server doesnt usually have a gui but im adding one so my family can troubleshoot if i cannot

---

### Post by spacecheck on 2012-01-06
Sounds like you might have been better off simply connecting some network storage to your home router, with access control and dynDNS.
I've read an article indicating mainboards require an EFI ("Extensible Firmware Interface")-firmware (BIOS) in order to boot from GPT partitions, although it also states there are a few boot managers that can boot GPT partitions from a few mainboards without EFI-BIOS, citing Grub2 (since ver. 1.97) as being one of them.
If you are going to use a partition for (large) media files you could select "Large" as the type of sector format during the installation partitioning The are four options "Standard", "News", ?, and "Large", which I think relate to 1 KB, 4KB, 1MB and 4MB clusters (I believe larger sizes limit the number of available inodes but increase the respective read rate for larger fiiles).

If your mainboard does not have an EFI/UEFI BIOS and is unable to boot from a GPT partition (and a BIOS update to add the function is unavailable), perhaps your earlier query > Should i return it and get a couple smaller hard drives? would thus be better answered in the affirmative.

With two 1 TB drives you could set up a RAID 1 (mirroring) and could partition them without using GPT.

With a NAS attached to the router,  you wouldn't have to boot from it and wouldn't have to have a server running all the time.

Good luck!

---

### Post by dRounse on 2012-01-07
Ok, i decided to use the 120gb as the OS, and i formatted the 2tb as ext3 and mounted it  but i want to make the server use the 2tb, as in dont save anything to the 120gb, but i was following a tutorial and i installed samba and the tutorial kinda jumped a stepand just said you needed to add a back end password but never went intodetail onthat.

---

