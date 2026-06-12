---
title: "GRUB problem with XP Pro"
date: 2009-12-10
forum: General Help
---

### Post by bobsp on 2009-12-10
I've been using Ubuntu 9.10 installed on a USB flash drive on my work laptop (which normally runs XP Pro)since 9.10 was released (and 9.04 prior to that) with no problems. All ubuntu updates have been applied ok, without affecting the laptop's ability to boot into windows when the USB key's not there. Yesterday, I downloaded and applied some new updates, and now my laptop won't boot to windows without the USB key - it reports "Loading GRUB, no such disk, GRUB Rescue. On other threads, it suggests that I use the recovery console to run fixmbr and fixboot, but when I try booting using the XP Pro install disc, it doesn't let me get as far as the recovery console. I get a blue screen telling me there's a problem with the hard drive. I had a similar result trying to boot with the Ultimate Boot CD for windows.
If I boot with the USB key in the laptop, I get the GRUB menu, and I can select XP Pro from the list, and XP runs normally.

Any suggestions how I can fix the boot, so that the laptop starts without the USB key?

Thanks,
Bob.

---

### Post by lmarmisa on 2009-12-10
This command should fix your MBR problem:

```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```Best regards,

Luis

---

### Post by oldfred on 2009-12-10
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

When one of the updates was done grub saw both disks but thought the internal drive was the boot disk, so it overwrote that. You may also need to reinstall grub to the external just to make sure it is up to date.

---

### Post by bobsp on 2009-12-11
Thanks oldfred, but as i'd said in the original post, I can't get to execute the fixmbr or fixboot commands, as the Windows install disc won't boot for some reason.

Luis, could you please explain what that command is doing? Is it writing a copy of the MBR of the flash drive to the hard drive MBR? If so, what will that do?

Thanks for your help,
Bob.

---

### Post by lmarmisa on 2009-12-11
Hi Bob,

That command writes the first 404 bytes of the MBR (Master Boot Record)  of the hard disk /dev/sda with a little loader program that is the same or very similar to the Windows XP loader. Probably, this program is not identical to the MS version in order to avoid infractions of copyright.

The structure of MBR defines a first region for this loader program (code area) and several other areas for other purposes, being the most important the table of primary partitions (64 bytes from address 446 to 509):

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

The mbr.bin file is only stored by Ubuntu, but it does not play any role in GNU/Linux.  This file is there only for the case that someone wants to unistall the grub loader and reinstall the Windows loader in the MBR.

If you wish, you can make a backup copy of the MBR code area before to the MBR update. 

```

cd $HOME # change dir to $HOME or any other directory where you have privileges for writing files
sudo dd bs=404 count=1 if=/dev/sda of=MBR.404bytes.backup.dd

ls -l MBR.404bytes.backup.dd # list the file

sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

```Now restart your computer and Windows XP will start normally.

Best regards,

Luis

---

### Post by bobsp on 2010-04-30
I finally got around to trying your suggestion - worked perfectly.  Thanks very much Luis !!

---

