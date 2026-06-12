---
title: "Stuck with installation"
date: 2010-11-24
forum: General Help
---

### Post by madmax.santana on 2010-11-24
I am trying to install Ubuntu on my Dell XPS.
I used UNETBootin to create bootable USB drive and started installation. But it go stuck at the very start. When I click "Forward" it just hangs there... The next screen never comes up. I have a screenshot of the scenario attached.
I thought UNETBootin had some problem and I re-created the live USB using the Universal Boot Installer, as mentioned on the Ubuntu download and install help page... But the same thing happened again... It sticks there... Doesn't more "Forward" at all...
Can anyone please suggest a solution?
I am afraid I don't have writeable CDs so I have to stick with USB... And yes, the .iso image passed the md5 checksum...


EDIT: Oh and yes!!! As soon as I click "forward" a crash report appears at the notification area. When I click it, it says, "Sorry, the program "parted_server" closed unexpectedly... Is there a bug in the Ubuntu Installer?

---

### Post by Quackers on 2010-11-24
Can you check the integrity of the burn? Maybe with F6 key at boot? There is an option on the Live cd to do this and I would imagine a usb burn has the same function.

BTW, no attachment shows

---

### Post by madmax.santana on 2010-11-24
Sorry, I forgot to attach. I edited later and attached the screenshot. Thanks a lot for notifying.
Yes, I verified the integrity of th burn and it says it's alright. :\
Also, it couldn't have burnt wrong 4 times... (:\ again)

---

### Post by Meezcore on 2010-12-01
I am having the same problem with my USB stick.
I want to install Ubuntu on my Acer 1825PTZ but it does nothing after pressing forward. And when i quit the installer I get the message:
 
Sorry, the program "parted_server"closed unexpectedly
 
Does anyone have a hint in where I can find some answers, because I'm a newbie and don't have a clue on where to start looking.

---

### Post by madmax.santana on 2010-12-01
I don't exactly have an answer for your question but I have a hunch that installation from USB is supported only for a narrow range of hardware. I was using an HP USB last time when I encountered this problem. However, later on, when I tried the same with a Kingston USB, everything worked fine. Try changing your USB...

EDIT: I am not sure, but as I said, it might only be my imagination. But that is how I got it working. Anyways, if you get an answer, please post it here as well as this thread is not solved yet.

---

### Post by Meezcore on 2010-12-02
Could you give me some info about the type of USB sticks you used?
I'll will check if I can find some differences that might explain why the one works and the other doesn't.
Tonight I'm going to try my external HD instead of an USB stick, maybe this will bring a difference.
 
Could you give me a layout of youre harddisk partitions?
Someone else mentioned on this forum that it could be a partitioning problem.
To many primairy partitions or such.
 
It's frustraiting that I can't go on after the forward button.
Because I want to play with that thing and Ubuntu :-)

---

### Post by mendhak on 2010-12-02
Any SD cards or peripherals in any of your slots? Remove them, try again.

---

### Post by Quackers on 2010-12-02
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
Code:

sudo bash ~/Desktop/boot_info_script*.sh

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Spyderkid on 2010-12-02
I suggest to use a CD instead for installation or a DVD for best results

---

### Post by Meezcore on 2010-12-02
I will also try external HD to exclude SD memory or USB Sticks.
If that doesnt work I'll use an external CD/DVD player on USB.
Ill try the script for information and post it in CODE .
 
To bad I don't have eSata on that thing.

---

### Post by madmax.santana on 2010-12-02
> Could you give me some info about the type of USB sticks you used?
I'll will check if I can find some differences that might explain why the one works and the other doesn't.
Tonight I'm going to try my external HD instead of an USB stick, maybe this will bring a difference.
 
Could you give me a layout of youre harddisk partitions?
Someone else mentioned on this forum that it could be a partitioning problem.
To many primairy partitions or such.
 
It's frustraiting that I can't go on after the forward button.
Because I want to play with that thing and Ubuntu :smile:

I used this USB...
 [IMG]http://www.ischinagoods.com/images/usb_device_drivers/Kingston-USB001_LRG.jpg[/IMG]
I don't have any specifics...

My HDD is like this.
sda1: Windows boot loader information (typical of Windows 7)
sda2: Windows Native (C: drive)
sda3: Linux Native (Ubuntu "/")
sda4: Extended partition with sda5: swap and sda6: another NTFS partition (D: in Windows)...
That's all... :)

---

### Post by madmax.santana on 2010-12-02
> Any SD cards or peripherals in any of your slots? Remove them, try again.

I don't think SD card reader has any connection with this because I think Linux does not support SD card readers yet... So it doesn't matter if you have an SD card inserted or not because Linux setup will not know... :\
P.S. I may be wrong.

> I suggest to use a CD instead for installation or a DVD for best results
That is not a solution. Me thinks...

---

### Post by Meezcore on 2010-12-02
When I take a look at the partition table under Windows 7 I see three partitions. The first is recovery, second is for Windows I dont know what for, and the third is for Windows as C:
 
I have made it smaller so I have an unpartitioned space of 75GB wich I intend to use for Ubuntu.

---

### Post by Meezcore on 2010-12-02
I have tried to install Ubuntu 10.10 desktop with a CD and an external USB DVD player.
And it worked.

I guess that USB Memory sticks don work at the moment.
Maybe something to check for people who understand this.

---

### Post by madmax.santana on 2010-12-03
> **Meezcore said:**
> When I take a look at the partition table under Windows 7 I see three partitions. The first is recovery, second is for Windows I dont know what for, and the third is for Windows as C:
 
I have made it smaller so I have an unpartitioned space of 75GB wich I intend to use for Ubuntu.
I think it is because you are using an OEM operating system. That means your Windows 7 came with the machine you are using. The extra partition (the one you don't know what for) is the recovery partition. Your computer must contain a software with which you can create a Windows recovery disk, which will reinstall all the content on your hard drive including Windows 7 and the hardware drivers for Windows in one go. All that installation data which you will put on that DVD(s) is actually on that extra drive.
If you think you should get rid of that extra drive I advise creating your backup disks, using some boot disk, erasing the existing partition table, creating a new partition table to your liking, and then re-installing all content with those recovery disks, directing it explicitly to leave the partition table untouched and modify only your sda2.

---

### Post by madmax.santana on 2010-12-03
> **Meezcore said:**
> I have tried to install Ubuntu 10.10 desktop with a CD and an external USB DVD player.
And it worked.

I guess that USB Memory sticks don work at the moment.
Maybe something to check for people who understand this.
That's good. Happy Ubuntu-ing... And yeah, I think the experts must look into the problem and find a solution.

---

