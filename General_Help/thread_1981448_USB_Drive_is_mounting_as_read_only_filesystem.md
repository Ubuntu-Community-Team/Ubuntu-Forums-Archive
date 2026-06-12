---
title: "USB Drive is mounting as read only filesystem"
date: 2012-05-16
forum: General Help
---

### Post by agrayray on 2012-05-16
Hi,

not sure why but all of sudden my one USB drive is always read-only when I try to use it in nautilus.  I am not sure if its mounting a read only filesystem..but it definately gets set that way if I try to use it in nautilus now, even if I try to run nautils from gksudo like below:

gksudo nautilus from the command line

So technically not sure if this is mounting as read only or its nautilus setting to it read only as I change it to read-write via the command  and that works until I  run nautilus on it.  Once nautilus runs it gets re-set to read only even from the command line.

Below shows some of my efforts from the command line..the USB drive is named JEDEN..it mounts as read-only, can not umount it (says it busy)...i can remount it as read-write ...and even create a directory...but when I open nautilus (shown here in command line..but happens from menus or anyway the same)..it gets set back to read-write...?

I actually use it for backup and have created and placed many files  there from the same computer (Ubuntu 10.10) many times before (I am even the owner of these files), but now, ALL the time I get errors saying that is a readonly  filesystem.

Does anyone have any ideas why is this is happening now..and how to correct it?


Thanks in advance!


rei@rei-ThinkPad-T410:/media/JEDEN$ pwd
/media/JEDEN
rei@rei-ThinkPad-T410:/media/JEDEN$ mkdir testing
mkdir: cannot create directory `testing': Read-only file system
rei@rei-ThinkPad-T410:/media/JEDEN$ man umount
rei@rei-ThinkPad-T410:/media/JEDEN$ umount '/media/JEDEN'
Unmount failed: Cannot unmount because file system on device is busy
rei@rei-ThinkPad-T410:/media/JEDEN$ man mount
rei@rei-ThinkPad-T410:/media/JEDEN$ sudo mount -o remount,rw '/media/JEDEN'
rei@rei-ThinkPad-T410:/media/JEDEN$ mkdir testing
rei@rei-ThinkPad-T410:/media/JEDEN$ cd testing
rei@rei-ThinkPad-T410:/media/JEDEN/testing$ ls
rei@rei-ThinkPad-T410:/media/JEDEN/testing$ mkdir test2
mkdir: cannot create directory `test2': Read-only file system
rei@rei-ThinkPad-T410:/media/JEDEN/testing$ sudo mount -o remount,rw '/media/JEDEN'
rei@rei-ThinkPad-T410:/media/JEDEN/testing$ gksudo nautilus &
[1] 2419
rei@rei-ThinkPad-T410:/media/JEDEN/testing$ Initializing nautilus-gdu extension
** (nautilus:2421): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '2421'

(nautilus:2421): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:2421): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

rei@rei-ThinkPad-T410:/media/JEDEN/testing$ mkdir testing3
mkdir: cannot create directory `testing3': Read-only file system
rei@rei-ThinkPad-T410:/media/JEDEN/testing$

---

### Post by dcstar on 2012-05-17
> **agrayray said:**
> Hi,

not sure why but all of sudden my one USB drive is always read-only when I try to use it in nautilus.  I am not sure if its mounting a read only filesystem..but it definately gets set that way if I try to use it in nautilus now
......

Do a fsck on it.

---

