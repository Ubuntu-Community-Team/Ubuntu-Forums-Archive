---
title: "Grub2 boot menu displaying in spite of configuration"
date: 2009-11-15
forum: General Help
---

### Post by dwasifar on 2009-11-15
Since the last grub2 update from update-manager, I've been seeing the boot menu with a 10-second countdown, even though I'm not configured for it.  This is from my /etc/default/grub file:

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
# GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

GRUB_HIDDEN_TIMEOUT=0 should suppress the menu.  But it doesn't.  Or it didn't; I found a workaround, but it's not pretty.

I was playing around with settings in this file, trying to make it work, and I noticed that each time I ran update-grub it would complain about not being able to find a GRUB disk on /dev/sdc.  /dev/sdc is my old Jaunty install, which I moved to a different SATA connector and mounted in my filesystem for a while to make the transition easier.  It has 9.04 on it, but not grub2.  So update-grub would spit out about ten copies of the same error and then say "done," and I would have a new grub.cfg file.

As an experiment, I physically disconnected that drive and ran update-grub again.  It didn't like not being able to talk to /dev/sdc, and threw a lot of complaining errors, but finished eventually, and when I rebooted I did not get the boot menu.

I thought possibly if I disabled the drive probe I could achieve the same thing, so I set /etc/grub.d/30-os_prober non-executable and ran update-grub again.  It didn't complain, but it did result in the menu reappearing on boot.  So that didn't work out.

My surmise from all this is that grub2 presents you with the menu if anything seems to be missing from its default behavior - there's a drive with an OS that update-grub couldn't index, or it can't run 30-os_prober, or whatever - so it shows you the menu probably as a troubleshooting aid.  Unfortunately this means that I have to physically disconnect /dev/sdc whenever I run update-grub, and the proper way to do this would be to shut down, disconnect, boot up, make my changes, shut down again, reconnect, and restart (instead of living dangerously and hot-unplugging that drive as I did today). 

I have to say I'm not too impressed with grub2.  I don't see that distributing the configuration all over hell and gone is an improvement.  menu.lst could be a pain but at least it was self-contained and understandable, and easier to configure.  I'm not sure this is worth it to shave a few seconds off the boot time.

---

