---
title: "Cannot access internal hard drive (location ubuntu is installed). Busy"
date: 2011-01-16
forum: General Help
---

### Post by drazelian on 2011-01-16
I would have posted this inside the x86 section for more specific help, but apparently, I am not allowed...

Anyhow, I have a rather nasty problem. As it stands, I can not boot into ubuntu, nor recovery mode. I have important files on my internal laptop hard drive (dev/sda2/)  that I can not access. I am also not able to access my HD when i boot from a live cd, because it says it is busy and being used by something else.

I am relatively new to ubuntu/linux, and my installation of 10.10 had been going great for almost 2 months up until a few days ago. Ill provide a rundown of exactly what has happened.

It began by chaning my plymouth boot theme. I cannot provide the code I used because I do not know what website I got it from, and the code itself is locked away in my HD. I do know that I had successfully changed it 3-4 times before, and this time as was trying spinfinity. After changing it, it told me it was done, and complete.

I go for a reboot and after going through the splash screen the system just hangs. I looked up what to do, and I saw that I could remove "quiet" and "splash" from the boot command and bypass the plymouth screen. This worked, but then I restarted again to see if the change was applied for every boot, which it wasn't. I could also get in when the screen was blank and hanging by ctrl+alt+f1, then starting gdm from there.

So I waited till the next say to fix it, and accidently booted into recovery mode from grub. Instead of a command line, I got busybox. I am not sure whether or not this would have happened if i had chosen to boot normally. Anyhow, No matter which kernel I choose, recovery or not it always boots into busybox, each time saying ```
no init found: try passing init_bootarg
```, or something similar to that.

At this point, all i wanted to do was save my data, I could deal with a fresh install. So i booted up a live disc, and tried to access my hd from there. When I click on it I get
Unable to Mount Location: DBus error org.gtk.Private.RemoteVolumeMoniter.Failed: An operation is already pending.

After this I went to the disk utility, and tried to mount it (dev/sda2), and fix it, neither of which worked. I got this error: An error occurred while performing an operation on "248 GB Filesystem" (Partition 2 of ATA WDCWD2500BEVT-60ZCT1): The device is busy.

I also tried (from live cd) ```
sudo fsck /dev/sda2
``` but just got told that it could not fix it because the device was busy. It told me it may be open with another program, but it obviously isn't because it is not being used by anything else.

Gparted didn't offer anything helpful either

I desperately need what is on the hard drive. At this point I do not care at all about saving my OS, all I want to do is get what is on the HD off, then reinstall ubuntu.

What should I do? Sorry about the wall of text, I just think any specific detail may lead to what the problem is.

---

### Post by drazelian on 2011-01-17
bump

---

