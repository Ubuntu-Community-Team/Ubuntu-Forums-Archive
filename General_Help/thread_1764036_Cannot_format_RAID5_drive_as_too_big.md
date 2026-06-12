---
title: "Cannot format RAID5 drive as too big"
date: 2011-05-21
forum: General Help
---

### Post by chipppy on 2011-05-21
Good Evening

I am trying to format a 7TB RAID5 setup,  I get an error saying partition table exposed max length of *********, using GParted

I would like to know what I need to do so that I can format my 7TB storage drive into 1 partition and mount it?

My setup consists of 5 X 2TB HDD's using ICH10R BIOS chipset (FakeRAID). I have setup to RAID5 Drive in the BIOS (1 X 250TB bootable for OS Mythbuntu, and 1 X 7TB non-bootable for storage)
Mythbuntu (OS) is installed and working fine on the 250TB drive.  I am nor trying to format the storage drive to ext4 and mount into the filesystem.

I am using [https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive") as my guide on how to format and mount.

I got the following and couldn't work out which was the 2 RAID5 drives I was using
> chipppy@chipppy-MythTV:~$ sudo lshw -C disk
[sudo] password for chipppy: 
  *-cdrom                 
       description: DVD-RAM writer
       product: BDDVDRW CH10LS20
       vendor: HL-DT-ST
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk:0
       description: ATA Disk
       product: WDC WD20EARS-00M
       vendor: Western Digital
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 51.0
       serial: WD-WCAZA5990866
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000d2bf2
  *-disk:1
       description: ATA Disk
       product: WDC WD20EARS-00M
       vendor: Western Digital
       physical id: 2
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 51.0
       serial: WD-WCAZA5856439
       size: 1863GiB (2TB)
       configuration: ansiversion=5 signature=000d5470
  *-disk:2
       description: ATA Disk
       product: WDC WD20EARS-00M
       vendor: Western Digital
       physical id: 3
       bus info: scsi@3:0.0.0
       logical name: /dev/sdc
       version: 51.0
       serial: WD-WCAZA5856363
       size: 1863GiB (2TB)
       configuration: ansiversion=5
  *-disk:3
       description: ATA Disk
       product: WDC WD20EARS-00M
       vendor: Western Digital
       physical id: 4
       bus info: scsi@4:0.0.0
       logical name: /dev/sdd
       version: 51.0
       serial: WD-WCAZA5991324
       size: 1863GiB (2TB)
       configuration: ansiversion=5
  *-disk:4
       description: ATA Disk
       product: WDC WD20EARS-00M
       vendor: Western Digital
       physical id: 5
       bus info: scsi@5:0.0.0
       logical name: /dev/sde
       version: 51.0
       serial: WD-WCAZA5990721
       size: 1863GiB (2TB)
       configuration: ansiversion=5
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@10:0.0.0
       logical name: /dev/sdf
       size: 3827MiB (4012MB)
       capabilities: partitioned partitioned:dos

I opened GParted and could see the 2nd 7TB drive no problem and it is unallocated.  I followed the steps> 1) Right-click on the white bar and choose "New."

2) For "New Size" the number should be the maximum allowable, to fill the entire disk.

3) Choose "Primary Partition"

4) Now decide on a filesystem. Use "ext3" if the drive will only be used with Ubuntu. For file-sharing between Ubuntu and Windows, you should use "fat32." If you are unsure, search around the wiki and forums for advice.

5) Now click Add to compute the partition. The graphical display should update to show a new partition covering the entire disk.

6) To finish, click "Apply," or Edit > Apply. The disk will then be partitioned and formatted. You may now close GParted. 

All but step 6 worked.  When I click apply a pop up appeared (looks like it trying to format the drive) but it immediately comes up the following error
> GParted 0.7.0 --enable-libparted-dmraid

Libparted 2.3
Create Primary Partition #1 (ext4, 7.03 TiB) on /dev/mapper/isw_bagafhadhf_MythTV-Storage  00:00:00    ( ERROR )
     	
create empty partition  00:00:00    ( ERROR )
libparted messages    ( INFO )
     	
partition length of 15103789056 sectors exceeds the bsd-partition-table-imposed maximum of 4294967295

I have tryed a few different Partition tables and all have the same problem of exceeding the max size.

How do I overcome this problem and format my 7TB Storage drive and mount it???

Cheers
Chipppy

---

### Post by prshah on 2011-05-21
> **chipppy said:**
> I would like to know what I need to do so that I can format my 7TB storage drive into 1 partition and mount it?

By default, GParted creates an msdos disklabel for uninitialized (new) "drives". However, msdos disklabel support tops out at a little over 2TB. For more, you need the disklabel to be GPT.

So, the first step you need to do in GParted for your new "drive" (RAID device) (before creating the partition) it to set the disklabel type to GPT. Click Device-Set Disklabel and set it to GPT. Then click "Create". You can then partition as normal.

Be aware that creating a new disklabel totally overwrites the MBR of the target hard disk. Since this is a non-bootable disk, it should not be a problem; but it a caveat to keep in mind.

---

### Post by srs5694 on 2011-05-21
Prshah is correct. I just want to add one more caveat: Although ext4fs has a theoretical filesystem size limit of 1 EiB, it's currently limited to 16 TiB because of limitations in support utilities. This is well above the 7 TB size of your current setup, but if you decide to increase it in the future but before the utilities are updated, this could become a problem. Thus, you might want to consider using XFS or JFS rather than ext4fs. XFS has a volume-size limit of 16 EiB, while it's 32 PiB for JFS. (I'd go with XFS; it seems to be more popular than JFS, and my own impression is that XFS is a bit more reliable.) AFAIK, the Linux tools for both can create and expand volumes to the  theoretical limits, provided you've got a big enough array.

---

### Post by chipppy on 2011-05-25
Good afternoon

That worked a treat.  I got the drive formated and mounted, after findout out to use ```
sudo lshw -l disk
``` to find the RAID names.

I now have a new problems installing Mythbuntu 11.04 onto the RAID.
I was playing witht he RAId to learn using a liveCD now I am trying to install Mythbuntu 11.04 onto this computer
I have 2 RAID partitions on the same 5 2TB HDD RAId system
250GB for the OS and the rest as storage (7.04TB)using the fakeRAID via a ICH10R chipset.

When I try to install all works fine until it tries to install the bootloader.  The install is trying to install  the bootloader onto /dev/sda (fit HD in my RAID), when using the format harddrive option.  
I cannot select any of the options 
egcontinue and install boot loader manually (I dont know how to do that anyway)
select a different drive
etc

When using the manual option I can select to install on /dev/dm-0 and to instal the bootloader on /dev/dm-0 but i then run into a problem of no root directory identified.  At this point I have the /dev/dm-0 (RAID OS) partition table as GPT and formatted in ext4.

Any ideas on how I can get the bootloader installed and therefore my Mythbuntu all installed.

Cheers
chipppy

---

### Post by prshah on 2011-05-25
> **chipppy said:**
> 
That worked a treat.  

Any ideas on how I can get the bootloader installed and therefore my Mythbuntu all installed.


There are (were?) some issues installing grub to a GPT volume (especially through Ubiquity). However, I have never worked with such large raid volumes and do not know the details.

Apparently, Grub2 can be installed manually, and grub classic needs some work around (a "/boot" partition?) but I am not exactly clear about it. Maybe a google search, or some other forum member can help you out.

I only post this so that you don't undo everything thinking that you might have done something wrong. I regret I cannot help further.

---

### Post by srs5694 on 2011-05-25
First, a point I missed in your original post: You're using motherboard-based software RAID (aka "fake RAID"), but if you're installing Mythbuntu, my guess is this is a dedicated MythTV setup. If so, I recommend against the motherboard-based software RAID approach. Although I have no personal experience with it, my impression is that it's much more trouble-prone than Linux's own software RAID. Also, the motherboard-based RAID will only be good on your current motherboard or models with a compatible implementation; so if you ever replace the motherboard, the RAID may stop working and you'll lose all your data. This isn't a problem with the Linux RAID implementation, although with that, if you want to switch from Linux to some other OS, you'll have problems. The only advantage of the motherboard-based RAID is that it works across OSes, which is important when dual-booting with Windows.

Second, I don't know how this interacts with either motherboard-based software RAID or Linux software RAID, but when installing GRUB on a GPT disk, it's best for the GPT disk to have a [BIOS Boot Partition,]("http://en.wikipedia.org/wiki/BIOS_Boot_partition") which is a small (32 KiB to 1 MiB) partition in which GRUB stashes some of its code. If you lack a BIOS Boot Partition, GRUB may fail to boot and sometimes it even refuses to install. It could be this is the cause of your immediate problem.

As prshah notes, GRUB Legacy required a separate /boot partition outside of the RAID setup to boot from a RAID array. GRUB 2 is supposed to work without that, but I don't know if there are exceptions or if that applies equally to motherboard-based software RAID and Linux software RAID.

Overall, then, I recommend you redo your RAID implementation:


[LIST=1]
[*]Partition your component disks using MBR. Be sure to use your RAID tools to remove the existing RAID markings on the disks. Use GNU Parted or GParted to redo the partitions; some tools will leave behind stray GPT data, which will cause problems.
[*]On at least one component disk, create a small (~200 MiB) /boot partition. (You could create additional similar partitions on other disks to balance it out, and use them to duplicate /boot or for future upgrade installations.) This step might not be strictly necessary, but it won't do any harm, either.
[*]Put the rest of the space into a big Linux software RAID array.
[*]Inside the RAID array, you have more choices. Personally, I'd use it as a big LVM space and create logical volumes for Linux and MythTV recordings. If you're not comfortable with LVM, you could partition it as GPT and create partitions like you've got now. Since GRUB will see the disks as MBR (which they are on that low level), you shouldn't need a BIOS Boot Partition in the GPT setup, although creating one won't hurt, either.
[/LIST]


OTOH, if you think you're close to getting it working as it is now and don't want to start from scratch, you can try to finish it. In that case, I'd recommend creating a BIOS Boot Partition in your current setup. It's small, so you may be able to squeeze it in to the existing partition scheme; or if not, a tiny resize operation should do the trick. You can then try re-installing GRUB, or re-install Mythbuntu and let its installer detect the BIOS Boot Partition.

---

### Post by chipppy on 2011-05-25
Good Morning

Yep I using fakeRAID from the motherboard.  I did read through [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto") in an attempt to use linux RAID but it was not detailed enough for my low level of understanding (I still learning the basics).

I building a dedicated MythTV system with the hope of adding in a fileserver to serve files for the familys 4 comptuer (I have 3 kids in school) and also emails, but that a lkater problem.
I wanted RAID as I store the family movies and photos, etc on here and I have already had a couple of expensice HDD Hardware failures (cost lots to recover birth movies from platters)  TheRAID give me a little more feeling of security.

I have not built anything in stone and I am happy to try anything.
I found this guide lastnight after posting my last reply to this thread [http://www.dedoimedo.com/computers/linux-raid.html]("http://www.dedoimedo.com/computers/linux-raid.html")
Do you think it will allow me to buld a Linux RAID and install Mythbuntu on it without to much difficulty?  I still learning the basics but I love to play around with the system to get a well setup system.  I am also a bit of a documentation nut so I like to create detailed how-to.
If this process works I can then create an update for the fakeRAID wiki page and hopefully help outothers.

Big thanks for your advice so far.

Cheers
chipppy

---

### Post by srs5694 on 2011-05-26
I can't say whether any given tutorial, especially one I haven't read, will help you (a person I don't know) successfully build a RAID array.

I can point out that RAID is not a substitute for backups. Instead of or in addition to RAID, you should back up your important data. For a MythTV system, that probably includes the OS installation with all its tweaks, the database, and any videos and other files you consider irreplaceable (family photos and videos, etc.). I wouldn't bother with TV recordings; they change too frequently and are too unimportant.

Most people these days seem to be using external hard disks as backup media. These are quick and convenient, but costs can add up if you want to do multiple backups. Recordable Blu-Ray discs might be an option for some systems, but I've not looked at the prices lately. Tape is the traditional choice, but although most types of tape are fairly inexpensive, tape drives are expensive.

---

### Post by athenroy on 2011-05-26
I agree with the backup idea.  Even with a 'fake" Raid, the way I understand it, you still only have one physical HDD.  If that fails, that's probably the end.  Same with the mother board.  I would think a smaller HDD and an external HDD for nightly backups of data would be a better solution, but a little late now, I guess.  I'm sure you are aware you can get any size internal HDD and a case to convert it to an external USB HDD.  Basically just plug it in to the interface in the case and that's about it.  Anyway, good luck and I hope you get it working.

---

### Post by chipppy on 2011-05-30
Good Afternoon

I have been called away from home for work so I have not had time to play lately but I will be hiome in 10days.

As to the USB back up idea.  I use that a little at the moment but seeing as my family are prolific camera users we have a huge amount of data (5TB worth last time I looked) in a mess of HDDs all over the place.
The one large storage computer allows me to clean up the mess into ione place, view the video/pictures, and via file serving play with (editing cleaning up rubbish etc)
The RAID allows me to have some security in the storage option (some redundancy)  Yes in a perfect world I would spend hundreds of dollars on a propery industrial RAID 6 system with proper RAID drive etc, but I dont have the money so I am using RAId as it was original designed (on the cheap/inexpensive)
Al always critical files (tax paperwork) is stored in multiple locations but these are relativly tiny when compared to a few hundred hours of home videos, and not an issue to have a few USB HDD's stored around the place.

In short I will keep trying to get this working.

As such do you have any ideas about how to overcome my install issue of the bootloader being installed onto /sda?

Do you know how I tell 11.04 to install the bootloader onto /dm-0??

I would take screen shots but I dont know how to get the screen shots onto aUSB stick during a live CD install.  If you know how to do that and want the screen shots please tell me how and I will get them for you.

Cheers
chipppy

---

### Post by chipppy on 2011-09-23
Good Morning

On a RAID5 freash install at boot after install complete  how do I fix
error: disk out of space
grub rescue>

*NOTE: This is a 64bit system and all install CD's are 64bit versions)*
I continue on trying to get this RAID5 setup of mythbuntu working.  I am now trying to use linux software RAID instead of the hardware fakeRAID.  As such I am using Xubuntu 10.10-Alternate CD.  

I still using 5 X 2TB HDD's to create a RAID5 setup
I have tried the same configeeratin both via GParted (off ubuntu 11.04 CD) and via the install Xubuntu 10.10-Alternate CD's partition system.

Each HDD is split into the follow partitions
1mb free (I am assuing this is the MBR space)
#1 100mb bios grub
#3 1000mb swap
#2 rest <2TB data
72.8kb free (it just a lazy few kb doing nothing)

Then RAID5 the swap and data partitions. the bios grub is left seperate for grub to be installed into.

When I setup this via GParted I used the GPT partition table, set the linux-swap flag but still use the instll CD to setup the RAID5

All times I have tried this the install goes well and the bootloader is installed on to all 5 HDD's. The install goes as per a normal install (I did a single HDD install to see if something different happened and it was all the same)

When I reboot the following comes up as the computer boots

> verifying DMI pool data............
error: out of disk
grub rescue>_

I did a search and this error seems to refer to a legacy issue to do with HDD sizes greater then 137GB.

I dont understand why this >137GB issue is causing my boot failure.

Can anyone see what I am doing wrong with the creation of my Linux software RAID5 system?

I have run out of things to try and get this system up and work please help

cheers
chipppy

---

### Post by jmate24 on 2011-09-23
add a boot partition of 300MB not 1MB and also put it in an ext2 file-system at the beginning of the first drive then Raid the rest of the space making sure that each partition size on each disk is 2TiB - 300MB.

another way is to use LVM. and that you still want a 300MB ext2 partition before the LVM setup but beware that you will have no redundancy as with Raid 5 but you can add as many Hard Drives as you want and the only problem is with space in your case.

---

### Post by chipppy on 2011-09-24
Good evening

I am a little confused here.
I have a 100mb bios grub partition on each disk.  
The 1mb free section is there automatically.  I cannot do anything with it and it is always there.  That is why i am assuming that it is the MBR space.

Looking at the GParted flag list today there is a bios grub boot flag and boot flag.

Are you referring to making a new additional partition of 300mb with the flag of boot, and therefore the following on each physical HDD.
1mb free (I am assuing this is the MBR space)
#1 100mb bios grub   not RAID
#2 300mb boot        ??????
#3 rest <2TB data    RAID5
#4 1000mb swap       RAID5
72.8kb free (it just a lazy few kb doing nothing)

If this is correct should I RAID5 the 300mb boot partitions together or leave then seperate?

Cheers
chipppy

---

### Post by srs5694 on 2011-09-24
> **chipppy said:**
> I am a little confused here.
I have a 100mb bios grub partition on each disk.

If by "bios grub partition" you mean a partition that's marked, in parted, GParted, or other libparted-based tools, as having a "bios_grub flag" set, then that's much bigger than it needs to be. libparted identifies [BIOS Boot Partitions](http://en.wikipedia.org/wiki/BIOS_Boot_partition) as having the "bios_grub flag" set. GRUB 2 uses a BIOS Boot Partition to hold part of itself. These partitions can be as small as about 30 KiB (I don't recall the precise limit), but 1 MiB is a more common size because of partition alignment policies (see below).

That said, a 100 MiB BIOS Boot Partition does no real harm, other than wasting most of the disk space it's been given. Thus, if your partitioning system is working well in other respects, I wouldn't recommend repartitioning.

> The 1mb free section is there automatically.  I cannot do anything with it and it is always there.  That is why i am assuming that it is the MBR space.

Having just under 1 MiB free at the start of the disk is now normal for any disk, and it's not really the MBR space. The Master Boot Record (MBR) is the first partition on the disk. That's normally 512 bytes. On a GPT disk, the next 33 sectors normally contain the primary GPT header and the primary partition table.

The first partition usually begins at sector 2048, leaving a gap of close to 1 MiB between the partition table and the first partition, in order to align the partition on a 1 MiB boundary. This is done because SSDs, some types of RAID arrays, and Advanced Format hard disks all perform best when partitions are aligned on certain power-of-2 boundary values, ranging from 8 sectors (4 KiB) to about 256 KiB. Aligning partitions on 1 MiB (2048-sector) boundaries ensures proper alignment for all these types of disks, and gives a bit of "fudge factor" in case the user is using something that's very exotic (or some future technology) that works best with such alignment.

You *can* create a partition in this space if you like. In fact, some uses might make sense; for instance, the performance problems with improper alignment would be so tiny as to be unnoticeable on a BIOS Boot Partition. That said, there's also little or no practical reason to try to cram something in there; 1 MiB is so tiny that's it's barely worth mentioning today. Also, not all partitioning tools will permit creating a partition in that space.

> Looking at the GParted flag list today there is a bios grub boot flag and boot flag.

The bios_grub flag is for the BIOS Boot Partition, as I've already noted. The boot flag, on GPT disks, sets the partition's type code to that for an [EFI System Partition (ESP),](http://en.wikipedia.org/wiki/EFI_System_partition) which is used by EFI and UEFI firmware to store boot loaders, drivers, and other files that are used by the firmware. The ESP is usually 100-200 MiB in size, although Ubuntu creates tiny sub-100 MiB ESPs, and I recommend creating them a bit bigger -- say, in the 200-300 MiB range. Whatever its size, the ESP should have a FAT32 filesystem, although most Linux distributions create them with FAT16. If your computer uses an old-style BIOS to boot, an ESP will be dead weight. If you use a UEFI to boot, though, it's critical that you have an ESP. If you're not sure if you use BIOS or UEFI booting, creating both partition types makes sense; the worst you'll lose is a few hundred gibibytes of disk space.

If you're using Linux's RAID tools, neither the BIOS Boot Partition nor the ESP should be RAIDed, although you should probably create redundant copies of these partitions on each of your disks.

---

### Post by chipppy on 2011-09-24
Good Morning

Thanks heaps for the indepth info.  For information I am using a Gigabyte GA-X58-USB3 motherboard which is reasonably new.  I do not know if my MoBo uses the UEFI or not, so I will assume that it will ands partition the harddrives as such.

From information have have made the following partitions (for each physical HDD) correct

#1 32mb bios grub not RAID FAT32  (32mb as this is the smallest GParted will allow)
#2 300mb boot not RAID FAT32
#3 rest ~2TB data RAID5 XFS
#4 1000mb swap RAID5     


If this is wrong please tell me, otherwise I am tryng install now and report back as to what happens (if the kids leave me alone long enough).

Again thanks heaps for the help

Cheers
chipppy

---

### Post by srs5694 on 2011-09-24
That looks good to me, although I would advise separating your one huge XFS partition into two partitions, one ~25 GiB for root (/) and the rest for /home (or wherever you need your huge amount of free space). This can greatly simplify certain types of system upgrades in the future.

---

### Post by chipppy on 2011-10-14
Good Afternoon

Sorry for the long delay in reply.  I got called away for work and have only just go back.

Right got it all working with a small change to the layout

#1 32mb bios grub not RAID FAT32 (32mb as this is the smallest GParted will allow)
#2 1200mb boot RAID FAT32 *********changed*********
#3 rest ~2TB data RAID5 XFS
#4 1000mb swap RAID5 

#2 is now RAID5 which makes sense since it is a mounted inside the filesystem and not external like the bios grub.

Right a few dumb traps that I fell into
1* Take notes
2* Forgot to check each partition was active when I ran alt-CD.  First time through it failed due to alt-CD defaults all partitions to 'do not use'.  Even though they are all setup and flagged you need to go in and change from 'do not use' to the correct set flags again.  A little annoying but easily fixed.
3* Patients people.  This huge size takes a long time to format load the OS onto.
4* Did I mention Take notes

Once I had the OS load onto the RAID system all was good.  Checked things out and played around a little and all seemed happy.  The is was update time.  Remember using 10.10
All went well until it came time for the grub updates.  Million options here on what to do with the grub update.  I wasnt sure and as I just wanted to findout what happens (so to gather info) I just selected a random option.  Turns out I selected the correct option,but cannot remember which one.  AND I didnt write down this option that I chose.  See where the Take Notes comes from.

For future reference does anyone know what is the correct option to choose for the grub update when I get this again.  (Dont think I am that luckly twice)

I have started installing Mythbuntu over the top of Xubuntu and running into few problems but these relate to adding Myth to Xubuntu and that is a different thread I think.

A huge thanks to all for there help and hope that this helps out someone one day.

I have to build a mates RAID system once I get this one sorted and I will endevor to write a step by step when I do that.

Cheers
chipppy

---

