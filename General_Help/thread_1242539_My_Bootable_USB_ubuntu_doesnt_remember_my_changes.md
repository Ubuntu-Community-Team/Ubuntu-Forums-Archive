---
title: "My Bootable USB ubuntu doesnt remember my changes"
date: 2009-08-17
forum: General Help
---

### Post by Teh H4rRy on 2009-08-17
I created a bootable USB stick with the wizard on the latest release of Ubuntu, i set it to have memory to save changes, it doesnt. I use Ubuntu on this netbook as i prefer it to Windows (Not my Netbook) is there a setting or command i can use for it to remember my changes?

---

### Post by Teh H4rRy on 2009-08-17
Anyone? no one has any ideas?

---

### Post by Mighty_Joe on 2009-08-17
I ran into several bugs with the USB Creator:
[Persistent partition size limitation]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/321544")
[Doesn't work unless a partition table exists]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/277865")
[Unclean unmount of persistent partition]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/125702")
Any one of those could cause the problem you are seeing. There are possible work-arounds posted in Launchpad and these forums (search!).
[This post]("http://ubuntuforums.org/showthread.php?t=1193680") contains alternatives to the USB Creator, including my preference, a full install to the flash drive.

---

### Post by pakki on 2009-08-18
> **Teh H4rRy said:**
> I created a bootable USB stick with the wizard on the latest release of Ubuntu, i set it to have memory to save changes, it doesnt. I use Ubuntu on this netbook as i prefer it to Windows (Not my Netbook) is there a setting or command i can use for it to remember my changes?

Well I tried live USB creator & set a space to save changes for my Ubuntu jaunty but it didn't 
Then I tried U904p method & using 1gb of casper-rw partition that come with this package but when I started to boot it said soe kind off buffer I/O error & ubuntu dont even started
So my friend in a nutshell I really am fed up with these methods which to me are nothing but fake & I am waiting rather for a portable windows which be quiet easy to install & save changes in my 4gb kingston USB

---

### Post by AmerNewbieInDE on 2009-08-18
i used uSBuntu live creator 1.5, in the options, create a persistent file, select how big you want the file, the program loads ubuntu on your usb and formats the persistent file. Then, just boot off the usb and select run persistent live, not just the live, it saved all i did and changed on the usb and never touched the hard drive.

---

### Post by C.S.Cameron on 2009-08-18
You can do a regular install to a (4G or larger) USB stick exactly the same as to internal hard drive, Just plug in your stick and disable your internal drive and run install, (ubiquity), from the Live CD. 
Here is another method I used to make a "persistent, disk image install:
Booted Live CD.
Plugged in flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started "Create a live usb startup disk", (usb-creator).
Selected "Discard on shutdown".
Pressed "Make Startup Disk.
When usb-creator finished, ran "gksu nautilus"
Selected disk / syslinux / text.cfg and added "persistent" as shown:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, removed CD, rebooted.
Changes were persistent.
Pakki:
To boot XP from USB see:
[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)

---

### Post by bodhi.zazen on 2009-08-18
See if these links help :

[http://www.pendrivelinux.com/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/usb-ubuntu-804-persistent-install-via-the-live-cd/)

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by Teh H4rRy on 2009-08-20
Thank you all very much for your ideas and suggestions, I got it working by Installing Ubuntu Directly to my USB stick, I Unplugged all other drives *aside from DVD drive* and ran the install, it works perfectly, every setting is kept, themes, bookmarks everything I could want from a portable OS. The only thing it cant do is install Ubuntu on another PC. No beef

---

### Post by bodhi.zazen on 2009-08-20
> **Teh H4rRy said:**
> Thank you all very much for your ideas and suggestions, I got it working by Installing Ubuntu Directly to my USB stick, I Unplugged all other drives *aside from DVD drive* and ran the install, it works perfectly, every setting is kept, themes, bookmarks everything I could want from a portable OS. The only thing it cant do is install Ubuntu on another PC. No beef

Well in theory you could install it via dd.

---

### Post by pakki on 2009-08-22
> **C.S.Cameron said:**
> You can do a regular install to a (4G or larger) USB stick exactly the same as to internal hard drive, Just plug in your stick and disable your internal drive and run install, (ubiquity), from the Live CD. 
Here is another method I used to make a "persistent, disk image install:
Booted Live CD.
Plugged in flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started "Create a live usb startup disk", (usb-creator).
Selected "Discard on shutdown".
Pressed "Make Startup Disk.
When usb-creator finished, ran "gksu nautilus"
Selected disk / syslinux / text.cfg and added "persistent" as shown:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, removed CD, rebooted.
Changes were persistent.
Pakki:
To boot XP from USB see:
[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)


Exremely thanks extremely thnx 
I will always get you appreciated in my university

---

### Post by C.S.Cameron on 2009-08-22
Pakki:
You might also try searching XP2USB ISO on Google or Mininova

---

### Post by pakki on 2009-08-22
> **AmerNewbieInDE said:**
> i used uSBuntu live creator 1.5, in the options, create a persistent file, select how big you want the file, the program loads ubuntu on your usb and formats the persistent file. Then, just boot off the usb and select run persistent live, not just the live, it saved all i did and changed on the usb and never touched the hard drive.

Respected sir, 
I tried this & the operations completed successfully.
But when I booted from USB after shutting down my PC I encountered errors right after the slide bar of Ubuntu boot screen disappears.
These errors were reiterating again & again saying something like
Buffer Device I/O error
however I really will giv a try to alternative method of partitiong my USB right from within Live Ubuntu cd

---

### Post by pakki on 2009-08-23
> **C.S.Cameron said:**
> You can do a regular install to a (4G or larger) USB stick exactly the same as to internal hard drive, Just plug in your stick and disable your internal drive and run install, (ubiquity), from the Live CD. 
Here is another method I used to make a "persistent, disk image install:
Booted Live CD.
Plugged in flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started "Create a live usb startup disk", (usb-creator).
Selected "Discard on shutdown".
Pressed "Make Startup Disk.
When usb-creator finished, ran "gksu nautilus"
Selected disk / syslinux / text.cfg and added "persistent" as shown:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, removed CD, rebooted.
Changes were persistent.
Pakki:
To boot XP from USB see:
[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)
Respected sir, 
I am facing two problem with your method 
1) the third partition  that is having name of home-rw be a ext3 or fat 32 type??  
However I make it ext3!!
2) ran "gksu nautilus" is what you said I ran it but it gave me some nasty errors; however all other steps were successfully accomplished including the editing of the *.cfg file

When I shutdown PC in ubuntu there for a second or so came I/O errors ( I haven't detached my USB at that moment ) however I ignored it 
I then booted from USB but I can't see any persistent mode in its welcome screen I thereby chose try ubuntu without any changes
Then the same thinh happened to me after slider vanished some buffer device I/O error keep reiterating

So I am really tired I happen to have tried all the methods available on net but to no avail I recommend you giv me your adress & I post you my USB!!:confused:

---

### Post by skyjacker on 2009-08-23
This site will help you. [http://www.pendrivelinux.com/category/flashdrive-installs-using-linux/](http://www.pendrivelinux.com/category/flashdrive-installs-using-linux/)    I use a usb drive "Thumbdrive" with ubuntu on it, and it has 4mb of persistant memory Casper-r file.

---

### Post by C.S.Cameron on 2009-08-27
Pakki:
The 3rd partition should work ok as ext3.
I found that sometimes it is difficult to make the casper-rw partition from the Ubuntu Live CD and may be easier using the Gparted Live CD.
The gksu nautilus part should be run from the Live CD.
I think that a page full of I/O errors is normal with a persistent disk image install but should not effect operation or persistence.
(A normal install to flash drive will not give these errors.
In the welcome screen "Try Ubuntu without any change to your computer" always comes up, However if you press F6 a line of boot options comes up. This line should read 
"noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --"
if the drive is persistent. Persistent will be missing from the above line if the drive is not persistent.
If persistent is missing it can be typed in at the end of the line and thhe boot should be persistent as long as there is a casper-rw file or partition.
You are welcome to PM me, just left click on my name and choose PM.

---

