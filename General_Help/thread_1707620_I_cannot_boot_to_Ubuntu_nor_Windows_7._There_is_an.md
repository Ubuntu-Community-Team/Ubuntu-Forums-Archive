---
title: "I cannot boot to Ubuntu nor Windows 7. There is an error. Help!"
date: 2011-03-15
forum: General Help
---

### Post by BinRoot on 2011-03-15
Hi,

I'm a long time lurker but I finally joined the forums to ask for help.

I installed Ubuntu 10.10 from a Live USB stick onto my 1TB external harddrive. Everything seemed to work so I removed the USB stick and hit enter to restart the computer as I was prompted. 

When booting up I get an error:

```
Error no such device <SOME HEX NUMS> 
grub rescue> 
```I turn off and boot back using my live USB Ubuntu stick. 

I open the terminal and type **sudo fdisk -l**


> Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       89723   720698911    7  HPFS/NTFS
/dev/sda2           89724       91201    11872035    c  W95 FAT32 (LBA)

Disk /dev/sdb: 1000.2 GB, 1000204885504 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      109028   875763570    7  HPFS/NTFS
/dev/sdb2          109028      121602   100998145    5  Extended
[B]/dev/sdb5          109028      121085    96846848   83  Linux
/dev/sdb6          121085      121602     4150272   82  Linux swap / Solaris[/B]

Disk /dev/sdc: 4103 MB, 4103937024 bytes
255 heads, 63 sectors/track, 498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x70a94399
[COLOR=#888888]

[COLOR=Black]This tells me Ubuntu was installed in /dev/sdb5 and /dev/sdb6

I want to uninstall Ubuntu from the external harddrive and be able to boot back to the Windows 7 partition. I will reinstall Ubuntu on a different computer after I fix this issue.

Someone please guide me to be able to use my Windows 7 partition again.
I'll be patient.[/COLOR]
[/COLOR]

---

### Post by drs305 on 2011-03-15
From the Ubuntu LiveCD, run the following to restore Windows. It appears your Windows partition is sda1. If not, change the command to the correct drive/partition:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Run the two commands above and don't worry about messages about fully-installing lilo.

If your BIOS points to sda, this should allow your Windows OS to boot.

---

### Post by BinRoot on 2011-03-15
Wow, I'm impressed by the quickness and accuracy of this answer. It worked! Thank you so much!

May I ask what might have caused the problem? I've been trying to install Ubuntu on this machine for a while and it would never work so I decided to install it on an external drive and you saw what happened. I'm confused why I can't get Ubuntu to boot from this machine. :/

---

### Post by Hugh971 on 2011-03-15
I had the same problem when installing. You probably need to enable booting from the device your trying to boot from in the BIOS.

---

### Post by drs305 on 2011-03-15
We've restored the Windows boot but we haven't altered any of the Ubuntu files. It may still be possible to get both OS's to boot.

If you boot the LiveCD and download and run the boot info script from the following link we may be able to see why your Ubuntu wouldn't boot. As was mentioned, it could merely be the boot order.

Once you run the script, please post the contents of the file, RESULTS.txt, it generates.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by BinRoot on 2011-03-15
Here is the RESULTS.txt output: [http://pastebin.com/dhXdnUdS](http://pastebin.com/dhXdnUdS)

---

### Post by Hugh971 on 2011-03-15
Did you check boot from that hard disk is enabled in the bios. I had the same problem you're having when I installed and that was the culprit. 

I think that's the most likely cause of the problem.

---

### Post by drs305 on 2011-03-15
Your Ubuntu boot files look fine. If you hadn't tried it earlier, you should be able to just change the BIOS boot order to boot first from sdb (the 1000 GB drive). Just enter BIOS, change the boot order so the 1000 GB  drive is booted first, and it should display the Grub2 menu.

The good thing is that, if it works, you will have Grub2 on your 1000 GB drive, which will allow you to boot both OS's; if you have a problem, you can change the boot order back to sda (the 750 GB drive) and you will be able to boot to Windows without having to make any other changes.

---

### Post by BinRoot on 2011-03-15
Hugh971,

I'm looking at my BIOS menus right now. Under the Boot menu I see the Boot device priority list and my external hard drive is listed as #2 (out of 2). I moved it to one and restarted and I got the same error. I moved it back to #2 and restarted and got windows 7 to show up again.

I'm not sure where exactly to enable/disable booting from harddrive. I think it's already enabled.

---

### Post by drs305 on 2011-03-15
> **BinRoot said:**
> Hugh971,

I'm looking at my BIOS menus right now. Under the Boot menu I see the Boot device priority list and my external hard drive is listed as #2 (out of 2). I moved it to one and restarted and I got the same error. I moved it back to #2 and restarted and got windows 7 to show up again.

I'm not sure where exactly to enable/disable booting from harddrive. I think it's already enabled.

In BIOS, check to see how large the BIOS reports the drive size. If it only reports a drive size of 137 GB or less your system may not be seeing the Grub boot files.

If the size is reported less than 137Gb, see if there is setting to enable large drives or some LBA setting.

---

