---
title: "Can't bootup Ubuntu"
date: 2010-06-16
forum: General Help
---

### Post by frankgirard903 on 2010-06-16
I have a dual boot PC (Ubuntu and Win 7). When I try booting Ubuntu, I get the following message:

  	 	 	 	 	 	  ntfs_attr_pread_i: ntfs_pread failed: Input/output error
 Failed to read NTFS $Bitmap: Input/output error
 NTFS is either inconsistent, or there is a hardware fault, or it's a
 SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windowss
 then reboot into Windows twice. The use of the  /f parameter is very
 important! If the device is a SoftRAID/FakeRAID then first activate
 it and mount a different device under the /dev/mapper/ directory, (e.g.
 dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
 for more details.
 Could not mount the partition /dev/disk/by-uuid/D81A3E541A3E303C. This could also
 happen if the file system is not clean because of an operating system crash, an
 interrupted boot process, an improper shutdown, or unplugging of a removable device without first unmounting or ejecting it. To fix this, simply reboot into Windows, let it fully start, log in, run 'chkdsk /r', then gracefully shutdown and reboot into Windows.  After this you should be able to reboot again and resume the installation. (filesystem = ntfs, error code = 13)
 

 BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
 Enter 'help' for a list of built-in commands.
 

 (initramfs) _


I think I did what the above says, to no avail. Win 7 boots up with no problem. I even tried accessing the drive with another PC, but the same message comes up. At worst, I want to move my pics, docs, etc. then reinstall Ubuntu. Any help, please...

---

### Post by cariboo on 2010-06-17
Did you run chkdsk /f in Windows, then reboot twice like the message above asks? You are getting the error message, because windows wasn't shut down properly.

---

