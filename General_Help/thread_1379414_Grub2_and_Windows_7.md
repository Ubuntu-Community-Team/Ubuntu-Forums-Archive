---
title: "Grub2 and Windows 7"
date: 2010-01-12
forum: General Help
---

### Post by rpgraca on 2010-01-12
I recently bought an Asus EEE with Windows 7 installed (they don't sell the ones with linux anymore? :/). I installed Ubuntu 9.10, and to do so, I needed to remove one partition, because there were already 4 primary partitions (C: (/dev/sda1) (windows system partition), D: (/dev/sda2) (which was empty and I deleted), /dev/sda3 a 10GB fat32 partition with Win Vista, I think, and a 16MB partition.
I deleted /dev/sda2 and created a ext4 and a swap partition and installed Ubuntu correctly. It's been working fine, but my mother uses the computer too, so I need to keep Win7. Choosing it in grub returned an error. Choosing Windows Vista (loader) in grub started a Windows recover, asking if i wanted to recover windows, and that it would erase all my files. I choosed "recover" and it said it was initializing, for some seconds, and then the computer restarted with no changes at all. I runned update-grub and it just made Windows 7 entry on grub menu desapear. How can I run Windows 7 along with Ubuntu? Please note that it's a netbook, so I dont have a CD drive in it.

---

### Post by Woody1987 on 2010-01-12
whats the output of sudo fdisk -l

---

### Post by Jose Catre-Vandis on 2010-01-12
I have an Asus nettop EB1012 and am successfully doing what you want to do. Had a bit of trouble to start with because of the quick boot features but eventually overcame these. I partitioned slightly differently, by creating an extended partition and then creating logical partitions in side that for Xubuntu and DATA (replacing the large DATA primary partition).

I installed Xubuntu and got grub booting OK to both Windows and Xubuntu. But I then went for the custom menu in grub (40_custom) to remove unwanted entries. It took a couple of boots to get everything to take, so that both the Xubuntu and Windows 7 entries showed up, but its working fine now.

I suggest you have a good read of [drs350's excellent Grub2 guide]("http://ubuntuforums.org/showthread.php?t=1195275") on the forum, and all should become clear regarding grub.

Here is my 40_custom file

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "XUBUNTU 9.10" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set d3496af7-fefe-422e-a1bd-beac336f92e8
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=d3496af7-fefe-422e-a1bd-beac336f92e8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}

menuentry "WINDOWS 7" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set dce08d3ce08d1dc0
	chainloader +1
}
```

You have to stop 10_linux and 20_memtest86+ and 30_os-prober from being executable to tidy up the menu.

Suggest you avoid trying to run the Vista (loader) entry, although it didn't seem to work, this will reinstall the default OS (W7) to factory settings

---

### Post by Woody1987 on 2010-01-12
I get the impression that the partition you deleted probably contained windows 7. Windows 7 uses two partitions, the first is a 100MB partition called System Reserved and another one which has the rest of the system.

---

### Post by Jose Catre-Vandis on 2010-01-12
Hmmm... quite possibly, for me the disk layout was:

/dev/sda1         Recovery @ 8GB ntfs (leave alone - you have no disc!)
/dev/sda2         Windows 7      ntfs (resize only using diskmgt.svc)
/dev/sda3         Hidden Fat32   fat  (at end of drive)
/dev/sda4         DATA           ntfs (delete this one)

Could be OP needs to wipe (except /dev/sda1) and start anew, but before doing so should investigate partition contents with livecd/liveusb

---

### Post by rpgraca on 2010-01-12
I tried Jose Catre-Vandis's suggestion, grub returned: 
error: No such device: dce08d3ce08d1dc0
Press any key to continue...

fdisk-l output is:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x061f1f04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10443    83882373+   7  HPFS/NTFS
/dev/sda2           10444       18149    61898445    5  Extended
/dev/sda3           18150       19456    10485760   1b  Hidden W95 FAT32
/dev/sda4           19456       19457       15712+  1b  Hidden W95 FAT32
/dev/sda5           10444       10567      995998+  82  Linux swap / Solaris
/dev/sda6           10568       18149    60902383+  83  Linux
Windows system partition was sda1, the one i deleted was empty an was shown in Windows as D:

---

### Post by Jose Catre-Vandis on 2010-01-13
So where is your Windows 7 installation if /dev/sda1 is the recovery partition, you should have another ntfs partition with Windows on it?

---

### Post by Kevbert on 2010-01-13
It looks like you trashed the Windows 7 partition. The hidden FAT32 drive is probably your boot drive. I've just gone through a similar procedure with Win 7 and Ubuntu 9.04 with Grub Legacy on a Revo R3610. With Grub2 you should also get two options of Windows Vista (loader) on boot-up (even though its Win7). One will be for System Recovery and the other to boot Windows 7.
See[COLOR="Red"][ this]("http://ubuntuforums.org/showthread.php?t=1379320")[/COLOR] on how to set-up your partitions. Post #4 will give you an idea on what you'll need to change in Grub2.

---

### Post by rpgraca on 2010-01-13
It seems ubuntu instalation screwd windows partition... sda1 was windows system partition and now has only 88MB used. The partition i deleted had 0MB used, it was a windows secondary partition which came empty by default. Anyway i can recover windows?

---

### Post by Jose Catre-Vandis on 2010-01-13
On my Asus, you need to press F2 on boot up to get boot options, then F9 to activate the recovery partition. Check your manual for your model [here]("http://support.asus.com")

Be prepared to lose everything and go back to square one. You may have to set the partitions back to how they originally were, I don't know how clever the recovery action is. My instructions say ensure there is a partition with +20GB. It also says to disable Boot Booster in the bios before trying to recover. You may/may not have this. Good Luck!

EDIT - direct from the EB1012 manual:
```
 Recovering your system
Using the hidden partition. The recovery partition includes an image of the operating system, drivers, and utilities installed on your system at the factory. The recovery partition provides a comprehensive recovery solution that quickly restores your system&#8217;s software to its original working state, provided that your hard disk drive is in good working order. Before using the recovery partition, copy your data files (such as Outlook PST files) to a USB device or to a network drive and make note of any customized configuration settings (such as network settings).

DO NOT delete the partition named &#8220;RECOVERY.&#8221; The recovery partition is created at the factory and cannot be restored by the user if deleted. Take your system to an authorized ASUS service center if you have problems with the recovery process.
                                                                                                                          Disable Boot Booster in BIOS setup before your perform system recovery from the hidden partition. Refer to the Boot Booster section for details.
                                                                                                                          1.	 Press <F9> during bootup (requires a recovery partition).
2.	 The ASUS Recovery System window appears. Select Recover system to a partition.
3.	 Select a partition with min. 20GB space and click Next.
4.	 Follow the on-screen instructions to complete the recovery process.
5.	 Restart the computer after the system recovery is completed.
6.	 Set up your language, time zone, keyboard, computer name, and user name to enter the Windows® OS.

```

---

### Post by rpgraca on 2010-01-14
I've been readig the manual and it says to do that. Yet, there is no Boot Booster option in Bios setup, only one Quiet Boot option in Boot Settings Configuration, which i disabled. Pressing F9 during boot doesn't make any difference, grub apears as normal after that. If I boot Windows Vista, which (i think) is the Asus Recovery Tool, and I choose Recover, it appears a message saying Initializing for about a minute, after that a terminal appears for few seconds and the computer restarts with no changes

---

