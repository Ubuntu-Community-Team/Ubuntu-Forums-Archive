---
title: "No Such Partition Grub Rescue"
date: 2011-07-28
forum: General Help
---

### Post by Suddent on 2011-07-28
Here is my situation,
I own a Sony Vaio VPCEB3AFM. It came with pre-installed Windows 7 Home Premium 64bit, no disks or anything. The product key is on the back of the laptop. I later installed Ubuntu, as I was beginning to take an interest in the potential of computers and began to explore with different Operating Systems. I installed it along side Windows 7. THEN, me being the dumbass I am, installed BackTrack 5 also. I then called Sony in attempt to restore my computer to factory defaults and just have Windows 7 as my only operating system. I shut my computer down and then hit F10 until the Vaio Rescue shows up. It was in the process of Restoring when it restarted and an error message came up. It reads, Error: No Such Partition Grub Rescue>. I have no idea what to do none of the OS boot up when I start it. I have no disks, I have only Ubuntu on a USB drive which I boot up by changing the BIOS blah blah. But when I do not have it in, the error message occurs. I would very much appreciate if anybody knows the solution to my problem and would be willing to help me out. I am not very good with computers and do not have too much knowledge so some terms I may not understand.

---

### Post by Mark Phelps on 2011-07-28
If your PC has an optical drive, you SHOULD have used the Backup feature to create and burn a Win7 Repair CD before you did the dual-boot stuff.  But since you can't boot into Win7 anymore, it's too late to do that.

One approach I would recommend (since Sony provided no disks), is to contact Sony, tell them your system crashed and you can't get into Restore, and order a set of full-recovery disks from them.  They will most probably charge you for them.

But once you get the disks, you should be able to restore your PC as it will boot from the disks, not the hard drive.

---

### Post by Suddent on 2011-07-28
> **Mark Phelps said:**
> If your PC has an optical drive, you SHOULD have used the Backup feature to create and burn a Win7 Repair CD before you did the dual-boot stuff.  But since you can't boot into Win7 anymore, it's too late to do that.

One approach I would recommend (since Sony provided no disks), is to contact Sony, tell them your system crashed and you can't get into Restore, and order a set of full-recovery disks from them.  They will most probably charge you for them.

But once you get the disks, you should be able to restore your PC as it will boot from the disks, not the hard drive.

Is there any way to erase Windows 7 then, I don't really need it. I have Ubuntu on a bootable USB and if I can get access to a different computer running Windows 7 could I burn whatever needed from there that way I don't have to pay?

---

### Post by Suddent on 2011-07-28
?

---

### Post by oldfred on 2011-07-28
You can replace the grub with a windows like boot loader in the MBR and see if that helps.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing testdisk with Synaptic.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.
[http://manpages.ubuntu.com/manpages/natty/en/man8/lilo.8.html](http://manpages.ubuntu.com/manpages/natty/en/man8/lilo.8.html)

---

### Post by Suddent on 2011-07-28
> **oldfred said:**
> You can replace the grub with a windows like boot loader in the MBR and see if that helps.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing testdisk with Synaptic.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.
[http://manpages.ubuntu.com/manpages/natty/en/man8/lilo.8.html](http://manpages.ubuntu.com/manpages/natty/en/man8/lilo.8.html)

I honestly have no idea how to do any of that =[

---

### Post by oldfred on 2011-07-28
You need to know how to use terminal to run commands.

Beginners guide:
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)
[http://ubuntuforums.org/showthread.php?t=790485](http://ubuntuforums.org/showthread.php?t=790485) (Newbie 101) 
[http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338) (Newbie Terminal Intro)
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885) (Terminal for Beginners) 
[http://www.solutionbeacon.com/CommonLinuxCommandsPocketGuide07.pdf](http://www.solutionbeacon.com/CommonLinuxCommandsPocketGuide07.pdf)

---

### Post by Suddent on 2011-07-28
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbbe37089

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10483712   27  Unknown
/dev/sda2   *        1306        1319      102400    7  HPFS/NTFS
/dev/sda3            1319       38914   301982720    7  HPFS/NTFS

---

