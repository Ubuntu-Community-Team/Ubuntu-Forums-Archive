---
title: "LIVE USB WONT BOOT : + Several problems (Many) ::Caution:Expect Angry Phrases"
date: 2010-03-21
forum: General Help
---

### Post by Hikayu on 2010-03-21
Ok, So right now I'm like really pissed off.

I'm that type of person who gives ALL the details, so if you hate reading, skip to the last few lines.

Ok, 19 of March, 2010, I heard that Ubuntu 10.04 Alpha 3 has been released, and I was like OMG~ Kewl! Proceeded to download because of the *"We guarantee 15 second boot time! XD"* thing. I've been using Ubuntu for exactly two years. It was 11 PM when I began the download. Everything was in ship shape. I left the thing on and displayed a note saying **"DONT TOUCH OR I'LL F***ING KILL YOU!"** On the screen. Simple enough.

Next morning : 20th March, 2010 : *"Great my birthday is tomorrow, and I have a new distribution. Yayz!"* thought me, when I woke up. Went to the room where my computer is situated and WTF?!? I saw no GUI and only a CUI! ARGH. It was my god damn sister who prematurely shut down the PC last night despite the warning signs I erected. And apparently during an important procedure too. And OMG my BDAY is tomorrow. So, being that guy who loves fixing stuff in awkward situations, I managed to successfully revert the thing in GUI mode. BUT WTH? 67% disk used up and "X cannot apply configurations" in other words **F***ING LOW GRAPHICS MODE**!!!. Ok, thought me. I can handle this.

I created another partition of 30 GB and decided to install Ubuntu 10.04 there. Than I'd transfer any files I need, destroy the old partition and combine the unallocated space with the 30 GB partition. "Great plan dude," thought me to myself.

Unfortunately, as life shows : Life isn't so easy, buster. My CD-ROM is utterly demolished and All I have is a crappy Kingston Data Traveler 2 GB smiling sheepishly at me. I decide to create a live USB, but it's not so easy.

I've attempted to use 54 different methods of creating a LIVEUSB but they all **JUST DON't WORK!** :(

It always says "BOOT ERROR" (In caps) when I try to boot the stupid thing. Any tuts? I've tried most of them.

---

### Post by Hikayu on 2010-03-21
Bump.

People hate me :/ . Is it my title?

---

### Post by davec64 on 2010-03-21
One thing that comes to mind is that sometimes the flag on the USB stick doesn't always get set to boot (happened to me). You can try ensuring that the flag has been set using GParted (assuming you can get to it!). For me the device then succesfully booted.


Best of luck! :)

---

### Post by Hikayu on 2010-03-21
Been there, done that. And no. I did mention that I've tried over 54 tutorials. I'm just hoping that someone can provide instructions for *MY* situation.

---

### Post by MelDJ on 2010-03-21
did your sister turn off the computer while you were downloading ubuntu or while your were installing it?

---

### Post by Hikayu on 2010-03-21
Think dude.

It wouldn't be THAT serious if it was downloading Ubuntu.
So obviously it was while installing.

---

### Post by uRock on 2010-03-21
If you want volunteers to help you, then you need to be a little more respectful.

---

### Post by Hikayu on 2010-03-21
Respectful as in being vulgar? Or was it my previous post?

I don't think I offended anyone save my sister.

---

### Post by MelDJ on 2010-03-21
your post was rude. thats why i edited this

its still in alpha/beta. what would you expect? ;)

---

### Post by uRock on 2010-03-21
The Beta1 released 2 days ago. Try posting in the Development sub-forum.

---

### Post by Hikayu on 2010-03-21
> **MelDJ said:**
> THINK DUDE 

its still in alpha. what would you expect? ;)

It ***WAS*** said to be stable. At least that's what I read. Nvm, I just gotta stop trusting people. :/

---

### Post by Hikayu on 2010-03-21
Actually, this post is more about getting a liveUSB. The story bout my sister was only there as a back story :)

---

### Post by MelDJ on 2010-03-21
> **Hikayu said:**
> It ***WAS*** said to be stable. At least that's what I read. Nvm, I just gotta stop trusting people. :/

[http://www.ubuntu.com/testing/lucid/alpha3](http://www.ubuntu.com/testing/lucid/alpha3)

from there: 
**This is an alpha  release. Do not install it on production machines. The final stable  version will be released on April 29, 2010.**

---

### Post by Hikayu on 2010-03-21
> **MelDJ said:**
> [http://www.ubuntu.com/testing/lucid/alpha3](http://www.ubuntu.com/testing/lucid/alpha3)

from there: 
**This is an alpha  release. Do not install it on production machines. The final stable  version will be released on April 29, 2010.**

_Production_ Machines.

Thanks. Aren't they referring to servers?

---

### Post by MelDJ on 2010-03-21
> **Hikayu said:**
> Actually, this post is more about getting a liveUSB. The story bout my sister was only there as a back story :)

after going through 54 ways, why don't use karmic for another week and install lucid when it is released officaily and stable?

---

### Post by Hikayu on 2010-03-21
> **MelDJ said:**
> after going through 54 ways, why don't use karmic for another week and install lucid when it is released officaily and stable?

Whats the point if I can't even GET a live USB? Still, good point.

But getting the USB to work is kinda more important.

---

### Post by MelDJ on 2010-03-21
> **Hikayu said:**
> _Production_ Machines.

Thanks. Aren't they referring to servers?

 i think its for computer which are used daily and are important

---

### Post by rahilm on 2010-03-21
Did you try any other distro as a Live-USB?? Does a live-usb of karmic boot?

---

### Post by Hikayu on 2010-03-21
Yep, done them b4

---

### Post by rahilm on 2010-03-21
Well then it is not a hardware problem. Unlike my USB disk. Which refuses to become bootable and always displays that "Cannot boot form device" error. I found that FAT filesystem was not formatted well. So i made a very small ext2 partition in the beginning. And it worked after that.

---

### Post by Hikayu on 2010-03-21
> **rahilm said:**
> Well then it is not a hardware problem. Unlike my USB disk. Which refuses to become bootable and always displays that "Cannot boot form device" error. I found that FAT filesystem was not formatted well. So i made a very small ext2 partition in the beginning. And it worked after that.

Please rephrase/emphasize this more.

This *migh*t be the answer to my problem.

---

### Post by DawieS on 2010-03-21
AFAIK, you cannot "copy" a CD ISO onto a USB disk, and expect it to boot and work the same. The file structures are completely different.

I think you can only create a bootable USB startup flash-drive from within an existing Ubuntu installation, which at some point in time must have been installed with either a CD, or correctly compiled USB startup flash-drive.

---

### Post by Hikayu on 2010-03-21
> **DawieS said:**
> AFAIK, you cannot "copy" a CD ISO onto a USB disk, and expect it to boot and work the same. The file structures are completely different.

I think you can only create a bootable USB startup flash-drive from within an existing Ubuntu installation, which at some point in time must have been installed with either a CD, or correctly compiled USB startup flash-drive.

Oh please,
I did remember mentioning the fact that I've been a Linux geek for over 3 years AND that I've done this before. ;)

---

### Post by jimmers on 2010-03-21
Try this tutorial:

  	 	 	 	 	 	  **[SIZE=4]How-to: Installing Ubuntu Linux on a usb pendrive[/SIZE]**

 This tutorial will show how-to install Ubuntu on a usb stick. Even though this tutorial uses Ubuntu as its base distribution, you could virtually use any type of Linux liveCD distribution.
 Being able to run Linux out of a usb bar is a great way to enjoy the live CD experience (being able to use Linux on any computer you might get by) and the big advantage of being easier to carry around than a CD.
 **[SIZE=4]1. Requirements[/SIZE]**

 In order to reproduce this tutorial, you will need a few items such as:  
 
[LIST]
[*]a ubuntu liveCD  	
[*]a usb bar of at 	least 1G  	
[*]a running Linux operating system  	
[/LIST]
 Now that you have all this, it is time to prepare you USB bar do host the Ubuntu liveCD files.
 **[SIZE=4]2. Setting up the USB disk[/SIZE]**

 **[SIZE=3]2.1. Finding the device[/SIZE]**

 In the first place, you need to plug your usb drive and check under which device it is associated. To find out the device, run:  
 $ sudo fdisk -l
 On my system, the device appears as being */dev/sdb*, I will therefore use /dev/sdb as a reference for this tutorial, please replace it accordingly to your system (might be sda, sdc ...).
Once you found your device, you are going to create the partitions.  
 Using the wrong device name might destroy your system partition, please double check
 **[SIZE=3]2.2. Making the partitions[/SIZE]**

 Make sure every of your already mounted partition are unmounted:
 $sudo umount /dev/sdb1
 and then launch **fdisk**, a tool to edit partition under linux:
 sudo fdisk /dev/sdb
 We are going delete all the partition and then create 2 new partition: one fat partition of 750M which will host the files from the live CD iso, and the rest on another partition.
 At fdisk prompt type *d x* where x is the partition number (you can simply type d if you only have one partition), then:
 
[LIST]
[*]*n* to 	create a new partition  	
[*]*p* to make 	it primary  	
[*]*1* so it 	is the first primary partition  	
[*]Accept the default 	or type *1* to start from the first cylinder  	
[*]*+750M* to 	make it 750 Meg big  	
[*]*a* to 	toggle the partition active for boot  	
[*]*1* to 	choose the 1 partition  	
[*]*t* to 	change the partition type  	
[*]*6* to set it to FAT16  	
[/LIST]
 Now we have out first partition set up, let's create the second one:
 
[LIST]
[*]*n* to 	create yet again a new partition  	
[*]*p* to make 	it primary  	
[*]*2* to be 	the second partition  	
[*]Accept the default 	by typing Enter  	
[*]Accept the default 	to make your partition as big as possible  	
[*]Finally, type *w* to write the change 	to your usb pendrive  	
[/LIST]
 Partitions are now created, let's format them.
 **[SIZE=3]2.3. Formatting the partitions[/SIZE]**

 The first partition is going to be formated as a FAT filesystem of size 16 and we are going to attribute it the label "liveusb".
 $ sudo mkfs.vfat -F 16 -n liveusb /dev/sdb1
 The second partition is going to be of type ext2 with a blocksize of 4096 bytes and the label **casper-rw**. Mind that it has to be labeled as *casper-rw* otherwise the tutorial won't work!.
 $ sudo mkfs.ext2 -b 4096 -L casper-rw /dev/sdb2
 At this stage, our usb pendrive is ready to host the liveCD image. Now, let's copy the files to the usb bar.
 


 **[SIZE=4]How-to: Installing Ubuntu Linux on a usb pendrive -- page 2[/SIZE]**

 **[SIZE=4]3. Installing Ubuntu on the USB stick[/SIZE]**

 **3.1. Mounting Ubuntu liveCd image**

 In the first place we need to mount our ubuntu iso. Depending if you have the .iso file or the CD, there is 2 different ways of mounting it.
 **3.1.1. Mounting from the CD**

 People using Ubuntu or any other user-friendly distro, might just have to insert the cd and it will be mounted automatically. If this is not the case:
 $ sudo mount /media/cdrom
 should mount it.
 **3.1.2. Mounting from an .iso image file**

 We will need to create a temporary directory, let say */tmp/ubuntu-livecd* and then mount our iso (I will be using a feisty fawn iso).
 $ mkdir /tmp/ubuntu-livecd
$ sudo mount -o loop /path/to/feisty-desktop-i386.iso /tmp/ubuntu-livecd
 Once the cd image is ready, it is time to mount the newly created usb bar partitions:
 **3.2. Mounting the usb bar partitions**

 Same here, you might be able to get both your partition by simply replugging the usb pendrive, partition might appears as: */media/liveusb* and */media/casper-rw*. If this is not the case, then you will need to mount them manually:
 $ mkdir /tmp/liveusb
$ sudo mount /dev/sdb1 /tmp/liveusb  
 All the partitions we need are now mounted, let's copy the files.
 **3.3. Copying the files to the usb bar**

 Let positionned yourself on the CD image directory (in my case: /tmp/ubuntu-livecd , but it might be /media/cdrom , and copy at the root of your usb first partition:
 
[LIST]
[*]the directories: 	'casper', 'disctree', 'dists', 'install', 'pics', 'pool', 'preseed', 	'.disk'  	
[*]The content of 	directory 'isolinux'  	
[*]and files 	'md5sum.txt', 'README.diskdefines', 'ubuntu.ico'  	
[*]as well as files: 'casper/vmlinuz', 	'casper/initrd.gz' and 'install/mt86plus'  	
[/LIST]
 $ cd /tmp/ubuntu-livecd
$ sudo cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz casper/initrd.gz install/mt86plus /tmp/liveusb/
 It might complain about symbolic links not being able to create, you can ignore this.
 Now let's go to the first partition of your usb disk and rename *isolinux.cfg* to *syslinux.cfg*:
 $ cd /tmp/liveusb
$ sudo mv isolinux.cfg syslinux.cfg
 change /tmp/liveusb according to your settings
 Edit syslinux.cfg so it looks like:
 DEFAULT persistent GFXBOOT bootlogo GFXBOOT-BACKGROUND 0xB6875A APPEND  file=preseed/ubuntu.seed boot=casper initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- LABEL persistent   menu label ^Start Ubuntu in persistent mode   kernel vmlinuz   append  file=preseed/ubuntu.seed boot=casper persistent initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- LABEL live   menu label ^Start or install Ubuntu   kernel vmlinuz   append  file=preseed/ubuntu.seed boot=casper initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- LABEL xforcevesa   menu label Start Ubuntu in safe ^graphics mode   kernel vmlinuz   append  file=preseed/ubuntu.seed boot=casper xforcevesa initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- LABEL check   menu label ^Check CD for defects   kernel vmlinuz   append  boot=casper integrity-check initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- LABEL memtest   menu label ^Memory test   kernel mt86plus   append - LABEL hd   menu label ^Boot from first hard disk   localboot 0x80   append - DISPLAY isolinux.txt TIMEOUT 300 PROMPT 1 F1 f1.txt F2 f2.txt F3 f3.txt F4 f4.txt F5 f5.txt F6 f6.txt F7 f7.txt F8 f8.txt F9 f9.txt F0 f10.txt Woof, finally we have our usb disk almost usuable. We have a last thing to do: make the usb bootable.
 **3.4. Making the usb bar bootable.**

 in order to make our usb disk bootable, we need to install *syslinux* and *mtools*:
 $ sudo apt-get install syslinux mtools
 And finally unmount /dev/sdb1 and make it bootable:
 $ cd
$ sudo umount /tmp/liveusb
$ sudo syslinux -f /dev/sdb1  
 Here we are :D , reboot, set your BIOS to boot from the usb bar and enjoy Ubuntu linux from a pendrive
 **4. Troubleshooting**

 If you are having trouble booting on the usb bar, this might be due to your MBR being corrupted. In order to fix it up, you can use lilo (I installed lilo on my box only for thid purpose).
 $ lilo -M /dev/sdb
 will fix the MBR on device /dev/sdb
 

Good Luck

---

### Post by DawieS on 2010-03-21
> **Hikayu said:**
> Oh please,
I did remember mentioning the fact that I've been a Linux geek for over 3 years AND that I've done this before. ;)

Could you please point out where you mentioned this! This may have been in some previous threads or posts you have made.

Don't expect any help if you yourself are not willing to give all details about your problem, and leave other forum members in the dark about your experience and abilities. :eek:

---

### Post by Hikayu on 2010-03-21
> **DawieS said:**
> Could you please point out where you mentioned this! This may have been in some previous threads or posts you have made.

Don't expect any help if you yourself are not willing to give all details about your problem, and leave other forum members in the dark about your experience and abilities. :eek:

Now please don't get pissed.

Also, there was a slight typo. It was two years, not three :P

Check the first post of this thread, TQ~

---

### Post by Hikayu on 2010-03-21
Now, for everyone : I'm getting somewhere now. I'm currently in the middle of it, but I'll post my results and how I did that. :popcorn:

---

### Post by rahilm on 2010-03-21
> **Hikayu said:**
> Please rephrase/emphasize this more.

This *migh*t be the answer to my problem.

This isn't exactly related to a live-usb. I have a very bad 8 gb usb disk which is wierd in many ways. Like, shows errors on being made bootable, my dvd-player refusing to recognise it etc.

I tried making a live-cd it worked!!. After a few months, i tried again. Surprisingly, it didn't work this time. even with the previous release.

I don't use live-sub disks anymore. I usually have many iso's on my usb disk and then i use grub2 to boot them.

The problem was actually installing grub in the partition. But grub and grub2 just refused to get installed. So I partitioned my disk. An almost 100mb ext2 partition in the beginning where i installed grub2 (which surprisingly worked now!!) and 7.9 GB to store ISOs.

So you can try making a small (100mb is not required) ext2 partition in the beginning. because I think FAT on my disk does not support messed up mbr. The only problem with this method is that your usb-disk will be unreadable in windows.

As an alternate solution, I might suggest shrinking and moving the current partition in gparted to the right. i.e to make a small 11~12mb of unpartitioned space in the beginning.

See if that solves your problem.

---

### Post by Hikayu on 2010-03-21
**[CENTER]ALRIGHT EVERYONE, I've figured out the problem;[/CENTER]**


[I]But you're going to find this weird.
As rahilm stated, there was a problem formating the USB to FAT32.[/I]

  So what I did was delete ALL partitions on the USB and create a EXT2 partition with the smallest size possible. (In this case 32MB.).

  I than created a FAT32 partition with the remaining unallocated space.

  I removed the EXT2 partition and merged the unallocated space with the FAT32 partition.

  I downloaded the latest ISO file for Ubuntu 10.04 Lucid Lynx.

  I downloaded UNetBootIn for Linux.

  I used it to apply the ISO file into the empty USB key.


**AND VOILA~ Problem solved.** If I knew the forums were this helpful I'll be coming here everyday.

Thanks rahilm

---

### Post by Hikayu on 2010-03-21
Writing from my new system :
[B]
LUCID LYNX RULES
[/B]
**[CENTER]I also hereby confirm that the cake (boot up speed) is NOT a lie. It takes 15 seconds to boot up. Thank you Canonical and Ubuntu for providing the best OS in the world~[/CENTER]**

---

### Post by Usabent on 2010-03-21
I am going to get ubuntu one more time. I dont have it on my pc anymore becuase i thougth there wont be any Ati drivers. Then i opend a thread. Some guy helped me and told me that My dirvers are already open sourced and ati dosent make the catalyst for linux on my grapchis card anymore.He said that i can still run it.

---

### Post by Hikayu on 2010-03-22
Umm, why did you post that *here*?

---

