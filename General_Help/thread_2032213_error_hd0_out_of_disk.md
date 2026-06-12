---
title: "error: hd0 out of disk"
date: 2012-07-23
forum: General Help
---

### Post by Simeo on 2012-07-23
My computer this morning booted up and just says:

```

error: hd0 out of disk.
grub rescue> _
```

Please help? It was running Ubuntu 12.04 64-bit perfectly fine before.

---

### Post by oldfred on 2012-07-23
Since it was working before I might try e2fsck on any or all ext partitions.


#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1


If that does not work, see this, but it is more for new installs with the issue:

Out of disk error add to grub install disk-module=ata or use Boot-Repair ATA Disk support
HOWTO: dualboot on big disk (BIOS limitations)
[https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk](https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk)
[http://ubuntuforums.org/showthread.php?t=1998257](http://ubuntuforums.org/showthread.php?t=1998257)
Large external drive still needed /boot at beginning:
[http://ubuntuforums.org/showthread.php?t=1888497](http://ubuntuforums.org/showthread.php?t=1888497)

---

### Post by Simeo on 2012-07-23
> **oldfred said:**
> Since it was working before I might try e2fsck on any or all ext partitions.


#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1


I typed "sudo e2fsck -c -p -f -v /dev/sda1" and now I'm waiting for a response from the computer. All I see is a white cursor right under the entry. *waiting*

Edit: 15 minutes later and still no response or sign of what's happening. Is this normal? *waiting*

---

### Post by oldfred on 2012-07-23
Did you do that from liveCD?

Is sda1 your ext4 partition?

---

### Post by Simeo on 2012-07-23
> **oldfred said:**
> Did you do that from liveCD?

Is sda1 your ext4 partition?

Yes, I did it from liveCD. sda1 is my main ext4 ubuntu partition. 

I'm still "waiting" by the way... :\

---

### Post by Simeo on 2012-07-23
Still nothing. It just sits there on the terminal. Anybody have any advice or help please? I can't even mount my hard drive from boot usb to backup files so I could do a clean reinstall.

---

### Post by oldfred on 2012-07-23
I assume BIOS sees drive.

What does Disk Utility show. If you click on drive  is it green or not? All I really know is drive needs to be green or it is failing.

---

### Post by Simeo on 2012-07-23
> **oldfred said:**
> I assume BIOS sees drive.

What does Disk Utility show. If you click on drive  is it green or not? All I really know is drive needs to be green or it is failing.

Sorry it took so long to reply. I had to borrow another computer to have some of the day's work done. 

Disk Utility shows a green dot and says: Disk has a few bad sectors

What should I do?

---

### Post by oldfred on 2012-07-23
That Disk Utility says drive is ok is good, but that nothing, grub nor e2fsck can open partition is not good. 

Does testdisk open partition or show errors?

Part of testdisk which is in the repositories or most recovery CDs.
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Simeo on 2012-07-24
> **oldfred said:**
> That Disk Utility says drive is ok is good, but that nothing, grub nor e2fsck can open partition is not good. 

Does testdisk open partition or show errors?

Running TestDisk now. Will update as soon as I'm finished.

Edit: The "Deep Scan" is currently at 73% and showing 13 partitions I didn't know about.... if I'm reading this correctly...

---

### Post by Simeo on 2012-07-24
Ok, I ran the deep search. TestDisk showed my current partition setup (Linux Boot + Swap) and detected all the deleted partitions from the past (WOW). I exited TestDisk successfully and terminal gave me this message:
```

TestDisk exited normally.
You have to reboot for the change to take effect.
```

I'm going to reboot now. :popcorn:

---

### Post by Simeo on 2012-07-24
Ok, after reboot I received nothing. Grub menu followed by black screen with blinking white cursor. I waited a very long time and a 32-bit looking "Ubuntu 12.04" showed up with four blinking dots and then black screen with blinking cursor. After a long while I shut down and now I'm booted into the USB drive again.

What should I do? I need to at least access my drive to recover some of the files I had before I could do a clean reinstall/wipe.

---

### Post by oldfred on 2012-07-24
If you hold shift key from BIOS until menu appears, do you get a menu?

You can try nomodeset or other boot parameters. 

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

### Post by Simeo on 2012-07-25
> **oldfred said:**
> If you hold shift key from BIOS until menu appears, do you get a menu?

You can try nomodeset or other boot parameters. 

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

Sorry I didn't reply earlier. Was feeling sick last night. Before I saw this I entered Ubuntu Recovery Mode, dropped to root, and ran dpkg to "repair" any errors. It found several bad sectors mainly effecting my gimp install, tmp folder, and pictures but I didn't notice any filenames connected to my business files. After pressing "y" numerous times dpkg finished and I rebooted. 

Still couldn't reboot to my hard drive but was able to mount the drive in the USB. I then transfered all my business files to my backup drive and all's well there. 

My largest concern is being able to isolate those bad sectors so they don't "spread" or cause more conflicts after I reinstall Ubuntu.

---

### Post by oldfred on 2012-07-25
A few bad sectors are not the end of the world, but I would maintain good backups. But if you start getting more & more then drive is starting to fail.

From Disk Utility click on drive and look at Smart Status. It has green for good and tracks many parameters for a hard drive.

---

