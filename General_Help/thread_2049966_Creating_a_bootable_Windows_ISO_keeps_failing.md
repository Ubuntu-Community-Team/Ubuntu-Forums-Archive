---
title: "Creating a bootable Windows ISO keeps failing"
date: 2012-08-29
forum: General Help
---

### Post by brandon89 on 2012-08-29
Hey guys, so I'm trying to create a bootable Windows 7 USB from an iso that I've used before.  I'm using WinUSB and everytime it keeps failing when it tries to install grub.  This is the error message it spits out:

> nstallation failed !
Exit code: 512
Log:
Formating device...
Mounting...
mount: warning: /media/winusb_iso_1346277516_31879 seems to be mounted read-only.
Copying...
Installing grub...
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a disk with multiple partition labels or both partition label and filesystem.  This is not supported yet..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
Error occured !
Syncing...
/usr/bin/winusb: line 78:  3928 Terminated              while true; do
    sleep 0.05; echo 'pulse';
done
Cleaning...
/usr/bin/winusb: line 78: 10167 Terminated              while true; do
    sleep 0.05; echo 'pulse';
done
Umounting and removing '/media/winusb_iso_1346277516_31879'...
Umounting and removing '/media/winusb_target_1346277516_31879'...


Any help would be great!  Thanks

---

### Post by Mark Phelps on 2012-08-30
Not familiar with this ... but from the messages, it looks like the app you are using is attempting to install GRUB -- which you definitely do NOT want on the bootable Win7 USB.

A cleaner way of doing this is to get access to an MS Windows PC and use the Microsoft tool linked below:

[http://www.microsoftstore.com/store/msstore/html/pbPage.Help_Win7_usbdvd_dwnTool]("http://www.microsoftstore.com/store/msstore/html/pbPage.Help_Win7_usbdvd_dwnTool")

---

