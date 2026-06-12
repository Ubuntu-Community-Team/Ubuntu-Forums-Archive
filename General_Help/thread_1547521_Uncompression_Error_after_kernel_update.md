---
title: "Uncompression Error after kernel update"
date: 2010-08-06
forum: General Help
---

### Post by guitarMan666 on 2010-08-06
After upgrading to a new kernel (via an official update from Ubuntu) today, my computer will no longer boot properly.  After rebooting to apply the update, my system ran its scheduled disk check (I think it's set to every 30 mounts or something like that). Errors were found and, as the message said, I "[Pressed] F to attempt to fix the Errors." They were fixed. Re-checking now in Knoppix reveals the file system is clean and it is, in fact, mounted as I post.

After leaving the computer alone for a while to check, it seems that it had rebooted without my intervention. It's a laptop on AC power and with a full battery so I ruled out a power interruption, but the screen says:
```
Booting from [my HD's UUID]...
Starting up...
Uncompression Error
  --System Halted
```

I figure "Ok, new kernel has an issue, I'll boot from one of the backups." I boot from the two previous versions (2.6.32-23 and 2.6.32-22) and both error out with a Kernel Panic and complains:
```
Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0).
```

So now I'm stuck with the prospect of backing up all of my data (a lot) and returning my computer to factory settings (Ubuntu 8.10) and re-upgrading or re-installing from scratch losing some of the Dell-supplied software.

I need to know if there is a way to non-destructively recover from this error. Any thoughts or ideas?

EDIT: This thread should be re-labeled [ubuntu], I must have mis-clicked.

---

### Post by cavalier911 on 2010-08-06
This could be caused by grub2 being misconfigured by the update.
Click the grub2 link in my signature and scroll down to Site Index/GRUB2 How to boot from CLI mode

---

### Post by guitarMan666 on 2010-08-06
> **cavalier911 said:**
> Your previous kernel is still installed,it should be listed on grub menu.Hold shift key if your menu's hidden to make it appear,highlight the older kernel and boot to it.

I don't follow. I already tried booting from the old kernels on my GRUB menu and those are the ones panicking.

---

### Post by cavalier911 on 2010-08-06
Nothing has changed about the old kernel,you know it works.
grub2's menu was updated when the new kernel was installed.
What if it has the wrong UUID for root ? 
You'd have this error > Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0).
Best solution would be How to reinstall grub2 from the livecd.
This topic is in the grub2 link in my signature

---

### Post by guitarMan666 on 2010-08-06
> **cavalier911 said:**
> Nothing has changed about the old kernel,you know it works.
grub2's menu was updated when the new kernel was installed.
What if it has the wrong UUID for root ? 
You'd have this error 
Best solution would be How to reinstall grub2 from the livecd.
This topic is in the grub2 link in my signature

I get what you're saying now. I did try one of the other older kernels (2.6.32-21) and it booted properly. Reinstalling the new kernel fixed the problem and I can now use the latest version of the kernel provided by Ubuntu.

---

