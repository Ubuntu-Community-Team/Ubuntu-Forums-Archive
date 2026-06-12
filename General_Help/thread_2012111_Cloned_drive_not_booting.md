---
title: "Cloned drive not booting"
date: 2012-06-28
forum: General Help
---

### Post by Crandles on 2012-06-28
Hey,

I recently purchased a new/larger drive and overnight I cloned my old one on to it. Unfortunately after replacing the old drive in the laptop I can no longer boot any of the OSes that were previously on it (I had both an Ubuntu install and a Windows 7 install). I was using a SATA to USB adapter to clone the drive. The weird thing is that when the old drive was in the computer I was capable of booting of the new drive (post-cloning) when it was attached through the adapter. A friend of mine recommended I try Hiren's boot CD so I've got a USB loaded with that. From using it I can confirm that the computer is capable of accessing the drive (I can view all the partitions and access the data no problem) so I think something went wrong with the MBR (I used Clonewipe 1.14, which I thought took care of that but maybe not). I don't get any specific error message per say but whenever I turn the computer on it immediately reboots after loading the BIOS (unless I select to enter the BIOS or have the USB key with Hiren's in). I don't know if this matters or not but the new drive was larger and I told Clonewipe to scale the partitions to the new size so their sizes have changed.

Thanks,
Graham

---

### Post by zero2xiii on 2012-06-28
Hay,

Sounds like your boot loader may be conky or not configured correctly.

To fix this, boot from a live ubuntu CD (not sure about Hirens boot CD/DVD, never used them before myself) and reinstall grub following the guides availible all over the internet such as:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

Dont let the "after windows install" fool you, just follow the steps and you should be on your way to success

Cherz

---

### Post by Crandles on 2012-06-28
Thanks. That seemed to do the trick for Ubuntu but now my Windows installs aren't booting (and there's two of them listed for some reason).

Boot info script output:
[http://paste.ubuntu.com/1064708/](http://paste.ubuntu.com/1064708/)

---

### Post by zero2xiii on 2012-06-28
Hmmm,

All seems fine. Although I might have missed something. Not sure.

What errors are you getting when trying to boot BOTH windows options? I asked this because I see:

> sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

which might explain why there are two entries listed. Curious but not suppose to cause you not being able to boot the windows partition. Also:

> => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Grub4Dos is installed in the MBR of /dev/sdb.

Looks like grub is configured correctly and looking and finding everything it wants (and since you can boot linux it seems that it is working)

> ### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 688E46218E45E860
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root D0B049DBB049C924
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

This also tells us the entries is actualy IN the menu. I dont see why it will not boot?

The issue might be:
> set root='(hd0,**msdos1**)'
However it checks out compared against the linux parameters.

I have no idea what else. I need the errors you get when booting windows to give some direction.

Cherz

---

### Post by Crandles on 2012-06-28
Thanks for the quick response.

The Windows error is kind of ambiguous. The screen says

[B]Windows Boot Manager
[/B]Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:

1. Insert your Windows installation disc and restart your computer.
2. Choose your language settings, and then click "Next."
3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

Status: 0xc0000225
Info: the boot selection failed because a required device is inaccessible.

I was just able to get a copy of my install disc (like 5 minutes ago) so I have yet to try the repair feature.

---

### Post by oldfred on 2012-06-28
If you changed the size of the NTFS partition, you have to run chkdsk and maybe fixBoot as NTFS partition's boot sector or PBR has to have the same start & size info as the partition table. Windows repairs should then fix it.

---

### Post by zero2xiii on 2012-06-29
Yep +1 for oldfred,

The moment any NTFS partition is resized windows see it as "corupted".

However, the 3rd option (in the error) might fix this. If not, boot from a windows CD into a recovery console (this will vary on version of windows CD you use and so forth but you want a console)

First you need to run chkdisk (I think this is how it is spelled under windows) on the drive and fix errors and recover corupted sections. (see the help of the command for the flags required)

You can try and reboot now and see if it works, or you can just skip and fix the MBR while you are inside the recovery console:

Run the fixmbr command on the drive with windows installed. Note that this MIGHT undo the grub re-installation aswell, but after the restart you will see. If windows boot fine but now grub is missing, just follow the [link]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") I gave you earlier aswell's instructions since this is essentialy what you have done (installed windows after ubuntu). After all of this, you should be back to your old system again :)

Cherz

---

### Post by Crandles on 2012-07-03
Thanks for the help! I can successfully boot into both OSes now.

---

