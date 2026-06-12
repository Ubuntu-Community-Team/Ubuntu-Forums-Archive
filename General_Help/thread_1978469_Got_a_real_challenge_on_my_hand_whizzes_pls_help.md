---
title: "Got a real challenge on my hand whizzes pls help"
date: 2012-05-11
forum: General Help
---

### Post by chinfa on 2012-05-11
Firstly it's my stupid fault:mad: I have a hp4510s pro-book I loaded on Ubuntu overwriting win7 because I wanted to see how it works vs win7 (not a dual boot system). Well last night I decided that utu didn't have the things which i needed or could have installed. So silly me went into the bios and used the sanitizer which cleaned the hard drive thinking that it would be a walk in the park to install win7 again. When that was complete, I poped in the win7 cd and restarted the system. Nothing happening then only to find that the boot sector went with the erase. So I cant get win7 or Vista to boot from cd to install the os. Only  thing that will work now is Ubuntu. So question is how can I uni-install ubunto so that I can fix the boot sector & create a new partition. Remember I said SILLY ME. Anybody with the know how please help!!!

---

### Post by Monotoko on 2012-05-11
Hey,

Is it a proper Windows 7 disk or is it a recovery disk? It should boot from disk regardless, even if nothing is on the hard drive or in the "boot sector". But HP might be using the typical way of "recovering", in which they save a section of the hard disk for a hidden partition where Windows installs from after you've booted from the disk, if you've wiped this partition Windows will not install using the recovery disk.

---

### Post by Mopar1973Man on 2012-05-11
Double check in the boot order and see if every is right like CD-ROM first and then hard drive. The boot strap on the CD/DVD should take care of everything if setup right. Also if the Windows Disk is original and not a copy it should work just fine. ;)

---

### Post by chinfa on 2012-05-11
Have the originals but no luck booting. Bios is cd then hdd. Is there a way to create a vista bootable partition through ubuntu?

---

### Post by chinfa on 2012-05-11
Is there any software out there which I can put in at bootup which will allow me to format the hard drive so that win vista or win7 can be installed then I can get over this hurdle? Thanks so far guys!!:)

---

### Post by traditionalist on 2012-05-11
> **chinfa said:**
> Firstly it's my stupid fault:mad: I have a hp4510s pro-book I loaded on Ubuntu overwriting win7 because I wanted to see how it works vs win7 (not a dual boot system). Well last night I decided that utu didn't have the things which i needed or could have installed. So silly me went into the bios and used the sanitizer which cleaned the hard drive thinking that it would be a walk in the park to install win7 again. When that was complete, I poped in the win7 cd and restarted the system. Nothing happening then only to find that the boot sector went with the erase. So I cant get win7 or Vista to boot from cd to install the os. Only  thing that will work now is Ubuntu. So question is how can I uni-install ubunto so that I can fix the boot sector & create a new partition. Remember I said SILLY ME. Anybody with the know how please help!!!

Get this;

[http://www.remastersys.com/](http://www.remastersys.com/)

run a backup and burn that to a DVD.  Now you can use that as a live disc to repartition your drive.

Install Gparted  or "Disk Utility" before you back up, ( both in various software centres etc), as this makes partitioning possible from the live disc.

---

### Post by LemursDontExist on 2012-05-11
The windows installer generally creates any needed partitions and writes the boot sector itself, so you shouldn't need to create a partition or boot sector before hand.  While you certainly could use an Ubuntu live disk to repartition your system, there's no way that that's your problem.

Booting from cd/dvd is actually completely independent of what's on your hard drive or whether you have a hard drive installed, and is determined exclusively by your bios.

So...  I can't say what's wrong with your system, but if the windows DVD doesn't boot then either the DVD is faulty, your bios is misconfigured, or you've got a hardware problem.  Since you said you went into the bios settings, I'd check to see if you accidentally changed something while you were in there.  I might also test to see if you can boot from that DVD on another machine just to be sure.

---

### Post by traditionalist on 2012-05-11
That's a point, but I had the same problem twice trying to boot a Windows DVD, the partition was locked in some way.   The other point is that the BIOS has to be set to boot the CD first.

---

### Post by chinfa on 2012-05-11
Double checked the boot sequence:
optical drive then hdd. My main headache is once I restart the notebook with the installation o/s (either vista or win7) nothing happens, then it goes to an Ubuntu screen for me to pick the the startup type. I just cant remove Ubuntu from the drive and get to install back a win o/s. So that's why I want some type of software which can clean the disc of everything (not the hp sanitizer), so that I can try to install a win o/s. In win environment you could always boot with the setup cd & repair but no go there.

---

### Post by chinfa on 2012-05-11
BTW if I cant get around this, I'm gonna drink some rum (I'm Jamaican) and go run the darn ghost out of this machine!

---

### Post by traditionalist on 2012-05-11
> **chinfa said:**
> Double checked the boot sequence:
optical drive then hdd. My main headache is once I restart the notebook with the installation o/s (either vista or win7) nothing happens, then it goes to an Ubuntu screen for me to pick the the startup type. I just cant remove Ubuntu from the drive and get to install back a win o/s. So that's why I want some type of software which can clean the disc of everything (not the hp sanitizer), so that I can try to install a win o/s. In win environment you could always boot with the setup cd & repair but no go there.

If you use the live DVD described above you can remove anything and repartition the drive.

Normally this should not happen, an external boot medium should always be able to boot and set up the drive itself, but I have had it happen a few times with windows dvd's that it would not.

---

### Post by jerome1232 on 2012-05-11
As others have pointed out, at boot time, neither Windows nor Ubuntu do a thing. It's all your computers BIOS, which checks each device it's told to check for a boot sector. According to HP, this is how you change the boot order on their computers.

[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&product=18703&docname=c00364979](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&product=18703&docname=c00364979)

> Configuring the boot order
The boot order can be configured on the Advanced tab in the BIOS settings menu. The steps for modifying the boot order may vary depending on the model of the computer.
NOTE:BIOS configurations vary depending on the computer. For further information on a specific computer, refer to the documentation provided with the computer or go to the HP Drivers and Downloads page . The BIOS settings are generally listed in the Maintenance and Service Guide.
Follow the steps below to configure the boot order on most computers.

    Turn on or restart the computer.
    While the display is blank, press the f10 key to enter the BIOS settings menu.
    NOTE:The BIOS settings menu is accessible by pressing the f2 or the f6 key on some computers.
    Select the Advanced tab using the right and left arrow keys.
    Use the up and down arrow keys to select Boot Order .
    Follow the on-screen instructions to change the boot order.

---

### Post by Mopar1973Man on 2012-05-11
I had a simular problem with a Sony Vaio laptop that refused to boot the Kubuntu Linux. What I did was found the restore to factory defaults saved and rebooted. Then came back to BIOS and set the stuff I absolutely neededand made sure of the boot order. BING! It was installing Kubuntu...

Like other said the hard drive has no bearing on if the CDROM is booted or not. If you want to make a point you could disable the hard drive all together and see if the CDROM boots. Kind of pointless since if it does then there nothing to install on... :lolflag: (Yes. I did this as a test too!)

---

### Post by ammofreak on 2012-05-12
Hi ):P
i will have mine with ice please...:lolflag:

---

