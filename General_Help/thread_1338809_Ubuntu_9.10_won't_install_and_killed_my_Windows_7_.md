---
title: "Ubuntu 9.10 won't install and killed my Windows 7 install."
date: 2009-11-26
forum: General Help
---

### Post by rmjohnson144 on 2009-11-26
I just installed Ubuntu 9.10 on my secondary hard drive and it wouldn't install.  I then switch to my Primary hard drive and when I boot I get a corrupted grub file.  It seems Windows 7 is using grub to startup?  

Anyway, I'd like to be able to boot my Windows 7 disk again.  I installed windows 7 on my secondary drive to recover my files, but some files I can't get without windows running.

Any help would be appreciated.
-=Mark=-

---

### Post by rmjohnson144 on 2009-11-26
I just tried to boot into windows 7 and get a new error:

```
GRUB Loading
error: no such disk
grub rescue>_
```

I think I may have lost the whole thing now from installing Windows 7 over Ubuntu 9.10.

Any help will be greatly appreciated.
-=Mark=-

---

### Post by JoshStrobl on 2009-11-26
use the windows 7 disk to repair your system. it will then start up in Windows 7 after you repair using disk

---

### Post by rmjohnson144 on 2009-11-27
Repair doesn't work.  I get some weird message that says it thihnks I have some device plugged in and it tells me to remove it and try again.  I have nothing plugged into it.

Is there a way to recover GRUB manually?  I relly need to get into windows as I have important emails and bookmarks.

-=Mark=-

---

### Post by balloooza on 2009-11-27
When you say switch hard drives, do you mean that you unplugged one drive and pluged in the other?

---

### Post by scottuss on 2009-11-27
Sounds as though you've just overwritten the Master boot record of the drive you were booting from before.

You should be able to overwrite GRUB with the Windows bootloader using the restore disk and getting a recovery console.

If you had both disks plugged in at the same time, which one did you install GRUB onto? The PC is still trying to boot from the same drive...

---

### Post by rmjohnson144 on 2009-11-27
I had both drives plugged in at the same time.  I switched in the BIOS to boot from my secondary drive and install Ubuntu 9.10.  Then it reported no bootable device and insert media and press enter to continue.

I then change to primary drive in windows to switch to windows 7 and then I get the GRUB menu(it seems it is the Ubuntu menu and overwrote the win7 boot menu), but it wouldn't boot Ubuntu or Windows 7.  

Next I unplug primary hard drive and install Ubuntu 9.10 on secondary drive and Ubuntu still won't boot.

next I just install windows 7 on the secondary drive so I have a working OS.

next I plug in both hard drives and try to boot from primary and lose GRUB completely.

so secondary drives is now my working win7 drive and my primary is my original win7 drive that won't boot at all and I get the broken GRUB prompt.

I used both win7 repair and restore last good boot, but it still won't boot after successful restore and repair just give me the device error.

sorry this seems a little confusing.  I'm in a hurry and out of time to thoroughly edit.

Let me know what doesn't make sense and I'll clarify.

-=Mark=-

---

