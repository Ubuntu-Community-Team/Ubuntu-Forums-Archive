---
title: "Full Ubuntu Netbook Remix on USB?"
date: 2010-05-24
forum: General Help
---

### Post by 8jwong14 on 2010-05-24
Hi everyone.  How can I install Ubuntu Netbook Edition 10.04 to a USB drive so I can run it on any computer.  I want the full version of it on my USB drive not just the live CD version.  I want to use Ubuntu on my school computers.

Basically, I wanted a  100% portable UNE that saves all settings, data, programs, etc and is still as fast as possible for a USB.

---

### Post by constellanation on 2010-05-24
I used unetbootin to install UNE to an sdcard for my install, worked great.

edit, actually i'm using it to burn an iso of ubuntu server edition right now for my new server parts that are in the mail...  hope it works as well.

---

### Post by zaivala on 2010-05-24
> **constellanation said:**
> I used unetbootin to install UNE to an sdcard for my install, worked great.

edit, actually i'm using it to burn an iso of ubuntu server edition right now for my new server parts that are in the mail...  hope it works as well.

I'm trying right now to do just this.  I downloaded the ISO file to an SD card.  I could not get my netbook to download Unetbootin (for some reason it's not finding the Internet, although it detects the wireless signal).  So, I took my USB jumpdrive (the same one that used to contain a bootable copy of UNR 9.10), cleared it, downloaded Unetbootin, put the ISO-containing SD card into another jumpdrive with an SD adapter.

I can get Unetbootin to recognize the ISO file, but it keeps trying to write to the USB drive that the SD card is hosted by (which is only 256 Mb).  I can't get Unetbootin to recognize the other USB jumpdrive... 

My computer lists the SD card as 7AE1-5A9E, the simple USB jumpdrive as 6051-2475.  I can't manage to equate 6051-2475 with "/dev/sd**".

=====

Well, in lack of an answer, I just copied the ISO to my desktop's hard drive, unplugged the host jumpdrive, and apparently UNetbootin works fine when there is only one drive to copy to.

---

### Post by C.S.Cameron on 2010-05-25
For a "Full" install:
Unplug internal HDD.
Insert Live CD, (or Live USB).
Insert target USB drive.
Boot Live CD.
Select Install Ubuntu at screen after languages.
Complete install process.
Your done.

Some people believe it is best to use manual partitioning to make a separate /home partition using ext2.

If you install proprietary drivers or heavily customize the install the USB drive might not work on every computer.

---

### Post by 8jwong14 on 2010-05-25
> **C.S.Cameron said:**
> For a "Full" install:
Unplug internal HDD.
Insert Live CD, (or Live USB).
Insert target USB drive.
Boot Live CD.
Select Install Ubuntu at screen after languages.
Complete install process.
Your done.

Some people believe it is best to use manual partitioning to make a separate /home partition using ext2.

If you install proprietary drivers or heavily customize the install the USB drive might not work on every computer.
So if I did this, would the target USB drive be fully portable and retain all files no matter the computer i use?

---

### Post by wilee-nilee on 2010-05-25
> **8jwong14 said:**
> So if I did this, would the target USB drive be fully portable and retain all files no matter the computer i use?

The variables are to far wide to answer that question. If you decide to do a full install though make sure on the last gui there is a advanced button click on it and make sure your installing grub to the mbr of the device .

---

### Post by C.S.Cameron on 2010-05-26
It will be just like an install to an internal drive but fully portable on most computers.
Some computers will not boot USB.
If you unplug your internal dive first you don't have to worry about where grub is installed.

---

### Post by wilee-nilee on 2010-05-26
Unplugging the drive is certainly a option, but just for a learning exercise I would still click on the advanced button in that final install gui so that you get the feel of always doing this always and understanding how grub is pointed and where it goes generally.

I never unplug drives I have mostly laptops and don't need to remove the HD to do a job easily accomplished by understanding how grub works, and just checking if it is going to the master boot record, of where I am installing to, or the relevant MBR.

---

### Post by C.S.Cameron on 2010-05-27
ld especially advise pulling your hard drive if you are a newbie and using a Windows machine and can't remember where your Windows install disk is.

---

### Post by 8jwong14 on 2010-06-02
> **wilee-nilee said:**
> The variables are to far wide to answer that question. If you decide to do a full install though make sure on the last gui there is a advanced button click on it and make sure your installing grub to the mbr of the device .
Sorry for taking so long to reply but thanks for replying.  So are you saying I can just stick my USB drive into my PC, then install UNE to the USB using a liveCD then select to install GRUB to the USB as well?  After this, will the USB UNE maintain all files and settings no matter which PC I use it on so it would be truly portable?

---

### Post by 8jwong14 on 2010-06-02
> **C.S.Cameron said:**
> It will be just like an install to an internal drive but fully portable on most computers.
Some computers will not boot USB.
If you unplug your internal dive first you don't have to worry about where grub is installed.
Sorry for taking so long to reply but thanks for replying.  So do I unplug my internal harddrive and install UNE to a USB using a liveCD?  Do I also install GRUB to the USB?

---

### Post by 8jwong14 on 2010-06-02
Can someone give me a basic 123 outline of how to install UNE to a UNE and still be fully portable?  Then we can argue on which parts of the process to change.  Thanks.

---

### Post by C.S.Cameron on 2010-06-02
> Sorry for taking so long to reply but thanks for replying. So do I unplug my internal harddrive and install UNE to a USB using a liveCD? Do I also install GRUB to the USB? 
Yes, It should be just like being able to take your hard drive with you.
If you unplug your hard drive, you can just install to the flash drive as normal. You don't need to worry about grub or other advanced option.
You might want to use manual partitioning so as to leave a FAT32 partition as your first partition in case you want to also use your flash drive for coping files from/to a Windows computer.

---

### Post by darkdragn on 2010-06-02
That would require a rather large jump drive, and the life of the jump drive will be next to nothing compared to a HDD. They just aren't made for that many r/w cycles. The best option would be to run an install to a VM, create a filesystem.sqfs off of the install, and make a casper partition. That will push the space taken by the os/install to about 30% of it's origional size, and allow persistent changes. If you would like to explore this option, please get ahold of me. That was all i did with my free time when i was on the USS Bataan in Haiti, these last few months.

---

### Post by C.S.Cameron on 2010-06-02
I have been running a Full install on a 4GB Kingston Traveler since the 4GB first came out.
I have never actually heard of anyone wearing one out 
Do the math.
10000 writes x 10 minutes to fill the device = 100000 minutes = 1667 hours = 42 work weeks, (@ 40 hour per week).
and nobody is going to spend 40 hours a week just writing to a thummb drive.
IF after two or three years you do brick the device it will only cost 5 or 10 dollars for a new one.

I'm not knocking a persistent, disk image install, except that you can't upgrade the kernel, it is just not the subject of this thread.

---

### Post by 8jwong14 on 2010-06-02
> **darkdragn said:**
> That would require a rather large jump drive, and the life of the jump drive will be next to nothing compared to a HDD. They just aren't made for that many r/w cycles. The best option would be to run an install to a VM, create a filesystem.sqfs off of the install, and make a casper partition. That will push the space taken by the os/install to about 30% of it's origional size, and allow persistent changes. If you would like to explore this option, please get ahold of me. That was all i did with my free time when i was on the USS Bataan in Haiti, these last few months.
I don't think it will have to be too large since the UNE is quite small and isn't a full system.  Also, I have a 8GB USB drive which seems sufficient.  I really want to use Ubuntu on my school PCs which should be able to run UNE.

---

### Post by 8jwong14 on 2010-06-02
> **C.S.Cameron said:**
> Yes, It should be just like being able to take your hard drive with you.
If you unplug your hard drive, you can just install to the flash drive as normal. You don't need to worry about grub or other advanced option.
You might want to use manual partitioning so as to leave a FAT32 partition as your first partition in case you want to also use your flash drive for coping files from/to a Windows computer.
Sorry but I don't understand what you mean by partitioning.  DO you mean partition my HD or the USB?

Ah yes...one more thing.  Can you give me a full process of how you did it with specifics please?  This may help other people who want to accomplish the same.

---

### Post by C.S.Cameron on 2010-06-03
I'll try to be brief:
Turn off and unplug the computer.
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu 10.04.
Fill in "Time Zone" and "Keyboard layout".
At "Prepare disk space" select "Specify partitions manually (advanced)".
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext4, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning, Ext4, and "Use as" = "swap area" then OK.
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Thats it, whew!

Edit:
Almost forgot,
Turn off computer and plug in the HDD.
Stick the side panel back on.

---

### Post by 8jwong14 on 2010-06-03
> **C.S.Cameron said:**
> I'll try to be brief:
Turn off and unplug the computer.
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu 10.04.
Fill in "Time Zone" and "Keyboard layout".
At "Prepare disk space" select "Specify partitions manually (advanced)".
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext4, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning, Ext4, and "Use as" = "swap area" then OK.
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Thats it, whew!

Edit:
Almost forgot,
Turn off computer and plug in the HDD.
Stick the side panel back on.
Do you mean to partition the USB drive?  Also, why do I have to partition it so many times even though its optional?

---

### Post by _Mark_ on 2010-06-03
Good post C.S.Cameron

Quick question, why the 1gig fat32? Is it just so you can use that space as a normal flash drive?

@8jwong14

Yes he does mean the usb, all you are doing is installing on the usb as you would a normal HDD so all the steps are the same, you really only need the / and swap partition but is good practice to have home on another partition so if you need to re install all you settings and such will still be their

---

### Post by 8jwong14 on 2010-06-03
> **_Mark_ said:**
> Good post C.S.Cameron

Quick question, why the 1gig fat32? Is it just so you can use that space as a normal flash drive?

@8jwong14

Yes he does mean the usb, all you are doing is installing on the usb as you would a normal HDD so all the steps are the same, you really only need the / and swap partition but is good practice to have home on another partition so if you need to re install all you settings and such will still be their
Yeah but is there a way to do it without also unplugging the HD?  Also how big should each of those partitions be if my USB drive is 8 GB

---

### Post by _Mark_ on 2010-06-03
> **8jwong14 said:**
> Yeah but is there a way to do it without also unplugging the HD?  Also how big should each of those partitions be if my USB drive is 8 GB

Ye just plug in the usb i run the installer when you get to the partitioning screen choose manual and select the usb drive to install on. After all it is just another drive

Assuming you want to use it all then 5 - 6 gig for / and the rest as swap or if you want a separate home stick to what  C.S.Cameron says in his guide

---

### Post by C.S.Cameron on 2010-06-03
Yeh, the FAT32 partition is just so you can use it as a normal flash drive on Windows machine.
Once you get it set up how you want it you can adjust partition size with gparted.
I always unplug my hard drive if I am installing from a Windows only machine cause I make lots of boo boos and I find it a hassle to dig out my Windows install CD so I can do a fixmbr. It's not a big deal to fix grub if you make a boo boo installing from a dual boot or Linux only machine.

---

### Post by 8jwong14 on 2010-06-04
> **C.S.Cameron said:**
> Yeh, the FAT32 partition is just so you can use it as a normal flash drive on Windows machine.
Once you get it set up how you want it you can adjust partition size with gparted.
I always unplug my hard drive if I am installing from a Windows only machine cause I make lots of boo boos and I find it a hassle to dig out my Windows install CD so I can do a fixmbr. It's not a big deal to fix grub if you make a boo boo installing from a dual boot or Linux only machine.
Thanks.  I'll try it out soon once I finish my homework.  :)

---

