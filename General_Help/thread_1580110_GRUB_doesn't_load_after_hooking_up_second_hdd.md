---
title: "GRUB doesn't load after hooking up second hdd"
date: 2010-09-22
forum: General Help
---

### Post by jslberto on 2010-09-22
Ok. I built my own computer a few months back.

-ATI Radeon 5xxx HD Video Card
-2 Hard drives, 1 is 750 gb, the other is 1 TB
-6 GB of RAM, triple channel memory
-Asus P6T SE LGA 1366 Intel X58 ATX Intel Motherboard
(if anyone wants the rest of the specs, let me know)

Anyway, I installed Windows 7 on both of my hard drives, and I recently decided that I wanted to install Ubuntu 10.04 (32 bit) onto my 1 TB hard drive. I used the entire hard drive, I didn't mind wiping Windows 7 off of one of them.

Ubuntu was successfully installed. Now, here's the problem.

In order for me to boot to Ubuntu at all, I have to disconnect the other hard drive all together. If the other hard drive is connected, something to the effect of the following pops up:

"Please insert a bootable media device and press a key or reboot..(can't remember the rest of it, it basically says put in a boot device or restart)

If I disconnect the Ubuntu hard drive and connect just the one with Windows 7, the same thing happens. 

I downloaded and burned a Windows 7 recovery disc because I figured that was the problem. I plugged in the external hard drive that contains my last Windows 7 backup, insert the CD, and it boots successfully to the system recovery settings. It automatically selects the System Image Restore, and has already detected the most recent system image on the external hard drive. However, when I click next to start the recovery, a window pops up saying that it has failed.

I tried the other options (startup repair, memory diagnostic, etc.) but all to no evail (or however it's spelled)

I should point out that I am a noob at computers and at Ubuntu.

Anyone's help with this issue is greatly appreciated, and while I know this may seem like a dumb problem to most people, I'm still learning, so please please take the time to dumb it down for me. Thanks very much if you decide to assist me.


-Josh

---

### Post by Bucky Ball on 2010-09-22
You would be advised to use MUCH more descriptive thread titles in future. You will have more success.

You have Windows on internal, Ubuntu on external? Unclear. You need to have Windows installed then install Ubuntu. It should detect there is another OS on the system and write it into the list that comes up with options at boot. The problem can come if your grub (the list of OS options at boot) is on the external drive and that is off or unplugged when you boot. If your computer is set in BIOS to boot from it and it's not there, error. Check in BIOS which partition you are booting from.

---

### Post by jslberto on 2010-09-22
Apologies. Can I rename the title?
Anyway, no both OS's are on separate internal hard drives. I can't access GRUB when they're both connected it goes straight to that reboot message

---

### Post by corrytonapple on 2010-09-22
Check the BIOS for the default boot drive. To get their you have to hit the key it instructs when the computer first boots up to the splash screen.

---

### Post by CharlesA on 2010-09-22
Changed the title to more reflect what problem the OP is having.

It sounds like you need to edit GRUB to point to the Win7 install on the 2nd hard drive.

What you can do is this:

Install GRUB on hard drive 1. Install Windows boot loader on Hard drive2.

Then select which drive you want to boot from when you start the PC.

---

### Post by jslberto on 2010-09-22
Thanks for the title change. BUT. the problem is that once I connect the second hard drive, grub doesn't load. In fact, nothing loads. it goes straight to that message listed above. And corrytonapple, thanks. I'm away from the computer for the night but if I'm not mistaken the default boot drive is the 1 tb one, which is the one with ubuntu

---

### Post by CharlesA on 2010-09-22
Changed it to more acurately reflect what the problem is, thanks.

I'm not sure why that's not working. I have a feeling that it has something to do with GRUB, but I am not sure.

---

### Post by perspectoff on 2010-09-22
I recommend you create a 100 Mb primary partition on disk 1 (using GParted from the Ubuntu LiveCD, for example).

Install a copy of Grub (I happen to like Grub Legacy for this) to this boot partition. The MBR will always and forever refer to this partition as having the master bootloader (never let an OS change the MBR, or if it does, merely reset the MBR to once again refer to this 100 Mb boot partition).

You can then usually edit the Grub configuration file in this boot partition from any OS whatsoever and set it to chainload the bootloaders for each OS.

Then you can have as many hard disks, OSs, and different bootloaders as you like and only have to deal with one main menu.

I don't quite know how to install Grub2 to a boot partition and have it work reliably as a chainloader, so I only use Grub Legacy for this purpose.

Grub Legacy refers to disk 1, partition 1 as (hd0,0) and disk 2, partition 1 as (hd1,0). Disk 1, partition 2 is (hd0,1), Disk 2, partition 2 is (hd1,1) and so on.

It is trivial to edit /boot/grub/menu.lst (for Grub Legacy, anyway) on the /boot partition so that all the OSs and their respective locations (in the (hd0,0) format) are listed and each set to merely chainload the individual OS/partition's bootloader.

A method I have of doing this is at

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

or

[http://kubuntuguide.org/Multiple_OS_Installation](http://kubuntuguide.org/Multiple_OS_Installation)

Once you have the boot partition set up, you can install any OS in any order you like. (Windows must always be installed into primary partitions). Windows will always overwrite the MBR, so you will have to reset it each time using the instructions at

[http://ubuntuguide.org/wiki/Multiple_OS_Installation#Reinstall_Grub_to_MBR](http://ubuntuguide.org/wiki/Multiple_OS_Installation#Reinstall_Grub_to_MBR)

During Ubuntu installation, it may do the same thing, or it might ask you whether to install to the MBR, depending on the installer version. If you are asked whether to install to the MBR, answer "no." Then just install the bootloader of Ubuntu to the same partition in which you are installing Ubuntu.

So, for example, if you are installing Ubuntu to SCSI Disk 2 partition 2, the partition will usually be called /dev/sdb2. That is where you should have the Ubuntu installer install the Grub2 bootloader. If you don't get the option or accidentally install it to the MBR as well, then merely restore the MBR with the same instructions above.

---

### Post by CharlesA on 2010-09-22
Please note that Legacy grub isn't being developed anymore. It has had patches to support EXT4 and whatnot, but it's not longer in active development.

You should use GRUB2. :)

---

### Post by perspectoff on 2010-09-22
> **CharlesA said:**
> Please note that Legacy grub isn't being developed anymore. It has had patches to support EXT4 and whatnot, but it's not longer in active development.

You should use GRUB2. :)

Yeah, whatever. GRUB2 is irritating as can be and causes endless problems for multi-OS systems.

Besides I'm not advocating getting rid of Grub2, I'm advocating quarantining it to the Ubuntu OS for use only for loading Ubuntu.

The problem with Grub2 developers is that they want Grub2 to be the master bootloader for all OSs, and it really doesn't work that well for that purpose.

For the very, very simple purpose of chainloading other bootloaders (including Grub2), Grub Legacy is simpler, more reliable, and highly recommended over Grub2 for this purpose.

That way, the chainloaded Mac bootloader can load the Mac OS. The chainloaded Windows bootloader can load the Windows OS. The chainloaded Grub2 bootloader can load the Ubuntu OS. Each bootloader can stay in its own partition and be updated, changed, or whatever, and not affect the other OSs.

The situation with Grub2 now is that it takes over duties for all bootloading and if it gets screwed up, no OS can boot. How many dozens of simultaneous threads on Ubuntu forums right now discuss this? Lots.

This poor guy's problems were created by Grub2. It even drove him to foolishly and unnecessarily erase a Windows 7 installation.

Now I have no objection to using Grub2 in the /boot partition as a simple chainloader in the same way, if you can post instructions how to do this simply. 

But so far I haven't seen such instructions floating around (and given the ease of using Grub Legacy this way, haven't looked too hard).

---

### Post by CharlesA on 2010-09-22
To each their own.

---

