---
title: "Can't resume from hibernation"
date: 2010-09-08
forum: General Help
---

### Post by Giraffro on 2010-09-08
Hi, I'm having trouble resuming from hibernation. The splash screen loads up with "Resuming from /dev/sda6" (this is the correct partition) and the HDD light shows it's reading the drive. It then stops reading and the loading animation starts up (I'm running Lucid). Then nothing, just the animation.

I recently updated initramfs-tools to 0.98ubuntu2~lucid as hibernation wouldn't work at all with the old version (see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/499940]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/499940")). I've also installed [this script]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/562484/comments/3") because of errors on hibernation.

Can someone help me? I've posted the output from recovery mode after hibernation below:

> Begin: Loading essential drivers ... done
Begin: Running /scripts/init-premount ... done
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done
Begin: Running /scripts/local-premount ... [    3.280440] PM: Starting manual resume from disk
[    3.281560] Freezing user space processes ... (elapsed 0.00 seconds) done.
[    3.281898] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[    3.306778] PM: Loading image data pages (126908 pages) ... done
[   11.121294] PM: Read 444708 kbytes in 6.96 seconds (63.89 MB/s)
[   11.121388] Suspending console(s) (use no_console_suspend to debug)
[   11.121606] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[   11.123474] pm_op(): usb_dev_freeze+0x0/0x20 returns -2
[   11.123477] PM: Device usb8 failed to quiesce: error -2
[   11.123707] PM: Restore failed, recovering.
[   11.149854] Restarting tasks ... done.
done.

---

### Post by rory526 on 2010-09-08
How much swap space do you have?
You have to have more than the amount of memory you have.

---

### Post by Giraffro on 2010-09-08
> **rory526 said:**
> How much swap space do you have?
You have to have more than the amount of memory you have.

I have 8GB of swap for 4GB RAM, so that shouldn't be a problem. Reading pm-suspend.log suggests the hibernation didn't fail, so the problem must be on resuming.

---

