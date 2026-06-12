---
title: "Windows lost the bootmgr."
date: 2009-07-20
forum: General Help
---

### Post by lszanto on 2009-07-20
Ok so I had one copy of xp on my computer ready to delete and at the time was ready for a fresh version so I quickly installed a new copy of windows. For some stupid reason windows decided to put all of my boot properties into the first installation, it did not ask me nor tell me any of this. I then proceeded to format my first installation to create some space and thus I now cannot boot into xp. I have tried rebuilding boot.ini and anything else but nothing works as it does not exist full stop. I am able to reinstall windows but this is an absolute last resort as if I go ahead with this chances are I will lose almost every single one of my ipod apps. If there is anything that I am able to do I am willing to try it.

Summary: Windows XP won't boot and gives a "bootmgr is missing, press alt+ctrl+del to restart".

Thanks in advance, Luke.

---

### Post by TeoBigusGeekus on 2009-07-20
Have you tried booting up with a winxp cd, going into recovery mode and giving fixmbr?

---

### Post by lszanto on 2009-07-20
Yep, the issue with that is it doesn't have any boot files or boot.ini to fix. If there was just an issue with boot.ini it would be fixable but it seems that I have no boot files that it can fix.

---

### Post by Deamos on 2009-07-20
Try this [http://www.chrisburgess.com.au/reinstalling-or-repairing-the-windows-xp-bootloader/](http://www.chrisburgess.com.au/reinstalling-or-repairing-the-windows-xp-bootloader/)

That should repair the bootloader.

Afterwards try this [http://support.microsoft.com/kb/330184](http://support.microsoft.com/kb/330184)

That should rebuild the boot.ini

Edit: Just realized the first link incorporated the boot.ini reconstruction.  If theres any problems with that, check the MS KB on rebuilding it.

---

### Post by lszanto on 2009-07-20
Nah I Just get this error:

Error: Failed to successfully scan disks for windows installations. This error may be caused my corrupt file system, which would prevent Bootcfg from successfully scanning. Use chkdsk to detect any disk errors.

I have checked multiple times, I have no disk errors. I think I'm just going to have to reinstall, I hate windows.

---

### Post by Deamos on 2009-07-21
> **lszanto said:**
> Nah I Just get this error:

Error: Failed to successfully scan disks for windows installations. This error may be caused my corrupt file system, which would prevent Bootcfg from successfully scanning. Use chkdsk to detect any disk errors.

I have checked multiple times, I have no disk errors. I think I'm just going to have to reinstall, I hate windows.

Hmm strange..  The only other thing I can think of is try to take a copy of someone elses boot.ini and manipulate it to match your system

Heres a sample found on MS's KB site.

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional" /fastdetect

```

Just alter the #s to match the location of your partition.

---

