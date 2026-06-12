---
title: "why can I no longer upload photos from my camera in 10.04 LTS?"
date: 2011-09-11
forum: General Help
---

### Post by PaulWhipp on 2011-09-11
Hi there,

I have a canon 30D which I've been using successfully with Ubuntu for years. I'm running 10.04LTS and I routinely run the updates every couple of weeks:

Sometime after August 8th, my usual import (plug the camera into USB and cut/paste the photos from the folder that opens) has stopped working.

The only software changes in that time have been the routine updates.

Now, the photos are still listed in the file browser when I plug the camera in but when I go to copy or look at them I get a -1 unspecified error. If I try to open the files in FSpot (never did this before - I was just trying to see if something would work - I get a could not acquire lock error).

Can someone tell me how to get this working again or how to report more information that might help get it working again?

---

### Post by HermanAB on 2011-09-11
Uhmmm... Maybe the camera is double mounted?
$ sudo mount
should give you a clue.

Unplug it, then replug it and look at the kernel messages with 'dmesg':
$ dmesg
To see what is going on with the USB subsystem.

Finally, try to unmount and mount it manually.

---

### Post by PaulWhipp on 2011-09-11
Hmm...
With sudo mount I get
```

~ $ sudo mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb1 on /media/shared_drive type ext3 (rw)
/dev/sda1 on /home type ext3 (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/paul/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=paul)
/dev/sdc1 on /media/Expansion Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```

This is the same before and after mounting so the camera does not appear in this list even though I can see the icon and the folder view :(

When I try "sudo mount -l" there is no difference in the list (except a label for the expansion drive).

I am guessing that these are the relevant dmesg lines (they are at the bottom)
```

[  972.872090] usb 1-5: new high speed USB device using ehci_hcd and address 4
[  973.018849] usb 1-5: configuration #1 chosen from 1 choice
[ 1131.092025] usb 1-6: reset high speed USB device using ehci_hcd and address 2

```

Looking at the camera icon, I can unmount it. If I select properties it tells me "The permissions of "Canon Digital Camera" could not be determined.

I don't know what command line options I should use to try to mount it manually.

I'm confused with this because it was working fine when I last used it.

When the camera times out, the icons and folder disappear. Reconnecting the camera does not work until after I restart the computer.

---

