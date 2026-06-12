---
title: "hdparm always shows drives frozen"
date: 2012-05-18
forum: General Help
---

### Post by sdpagent on 2012-05-18
Dear all,
I am trying to perform a 'secure-erase' on a drive as shown in the tutorial here: 
[http://tinyapps.org/docs/wipe_drives_hdparm.html](http://tinyapps.org/docs/wipe_drives_hdparm.html)
unfortunately I cannot get any of the drives (even the one that the OS is running which must be a bug) to not appear as 'frozen'.

example output:
[IMG]http://img1.uploadscreenshot.com/images/orig/5/13810045536-orig.jpg[/IMG]
I have tried putting the computer to sleep and waking it up, but it wont wake up. I have also tried rebooting the machine, but the drives will still show up as frozen directly after booting up.

I have also tried using the hdparm -y command to set into standby rather than sleep mode, which returns success but still shows frozen.

Whilst frozen, I cannot set the security password or perform a secure-erase as this will return
"... Input/output error"

Any and all help appreciated.

Regards
Stu

---

### Post by papibe on 2012-05-18
Hi sdpagent.

I haven't found a way to unfrozen a SSD without sending the machine to sleep first.

This is how I've done it: [How to securely erase an SSD drive using Parted Magic]("http://howto.cnet.com/8301-11310_39-20115106-285/how-to-securely-erase-an-ssd-drive/").

I hope that helps,
Regards.

---

### Post by sdpagent on 2012-05-18
> **papibe said:**
> Hi sdpagent.

I haven't found a way to unfrozen a SSD without sending the machine to sleep first.

This is how I've done it: [How to securely erase an SSD drive using Parted Magic]("http://howto.cnet.com/8301-11310_39-20115106-285/how-to-securely-erase-an-ssd-drive/").

I hope that helps,
Regards.

Unfortunately these aren't SSDs, and my computer wont boot back up from sleep...
They are two WDs and a Hitachi sata hdds.

---

### Post by sdpagent on 2012-05-19
An update which may or may not help. It appears that if I boot the computer without the drives in, and then plug them in after the machine has started, they are not recognised and do not appear when I run the command:
fdisk -l

I read online that hot swapping should be supported. Is there any reason to believe otherwise?

Stu

---

### Post by sdpagent on 2012-05-19
I discovered that the issue was that I did not have AHCI enabled in the bios. After turning that on, I was able to unplug and re-plug the drives in and they show up as not frozen

Stu

---

### Post by rustycar54 on 2013-01-31
> **sdpagent said:**
> An update which may or may not help. It appears that if I boot the computer without the drives in, and then plug them in after the machine has started, they are not recognised and do not appear when I run the command:
fdisk -l

I read online that hot swapping should be supported. Is there any reason to believe otherwise?

Stu

Back to the original issue:

BIOS's sometimes set the freeze state of a drive.  Once that is set, you are stuck and cannot erase the drive.  In order to "un-freeze" the drive you must 'reset' the drive WITHOUT letting the BIOS get involved.  Easiest way to do this is to power cycle the drive.

Of course, hot swap must work or the drive won't be detected by the OS, which is why you had to turn on AHCI.

In summary:

If BIOS 'freeze's a drive, your options are:
1 - 'thaw' (un-freeze?) the drive by power cycling JUST THE DRIVE and not the computer.
2 - get a BIOS that doesn't freeze drives.
3 - do not let the BIOS see the drive during bootup.

Rusty

---

