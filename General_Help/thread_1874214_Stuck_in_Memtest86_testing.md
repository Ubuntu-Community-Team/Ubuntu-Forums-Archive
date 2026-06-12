---
title: "Stuck in Memtest86 testing"
date: 2011-11-02
forum: General Help
---

### Post by tnanek on 2011-11-02
Okay, I have an Ubuntu Oneric Ocelot install (upgraded from a Natty install previoously). I shut down the machine due to a loss of power (I have a battery backup, so it was done in the regular manner).

Now when I try to reboot the machine, I can get to a boot device list, and when I select the hard drive, it goes directly into a Memtest86+ v4.20 screen testing my memory and/or hard drives. I first let it complete this until the Pass said 100%, and I noticed it was still going. Thus I rebooted the machine, it went right back to it from the start, and I let it go for about 2 or 3 hours and it was still running tests. I just tried rebooting it again with no luck in getting anything different. How do I stop this Memtest86+ testing when it gets to 100%? 

The configuration options don't provide much, there is a restart option, though that only restarts the testing, not the computer. Escape only makes the testing start again from scratch on the next boot.

I can't find a way to get to my desktop at all, and am lucky to have an alternative laptop available.

I can't even read the whole screen either.

---

### Post by Jouke74 on 2011-11-02
Oh I also got into this cycle a few times. It is because Grub is not configured to select from the menu by default. It starts the most recent updated kernel. Unfortunately with your powerdown probably the first two kernel entries got deleted or damaged, hence grub is always starting memtest (which you cannot quit without rebooting)...

option 1 to test : Please hold left shift when booting and see if you can get into the grub menu.

Use this commands if you know what they mean:
ls

ls (hd0,1)

root=(hd0,1)

-----or whatever your root is-----

-----keep ls ing until you find your root---



set root=(hdX,Y)

set prefix=(hdX,Y)/boot/grub

set

insmod /boot/grub/linux.mod

linux /vmlinuz root=/dev/sdXY ro

initrd /initrd.img

boot


Option 2: 

Please use a Ubuntu life cd to start from. 

- Reinstall grub from the life CD on your harddrive (the right one) and check if your kernels are working.

Edit /etc/default/grub also on your harddrive to show the menu by default. So set hidden menu to false, set timeouts to 10. 

If your kernels are fine this should fix the stuff.

IN ALL CASES BE CAREFUL NOT TO ERASE YOUR HD!

---

### Post by Jouke74 on 2011-11-02
Also read this still:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by tnanek on 2011-11-02
I reinstalled my grub-pc package, as per [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

but there was no change, still only running memtest and no other options.

Now I suppose I'm down to seeing if I can repair the kernal, or duplicate the default install's /boot directory... any tips or should I just reinstall (an option, though not a favorable one...).

Right now i'm running off the liveCD and going to chroot into the system again, as a precursor for doing anything.

---

### Post by tnanek on 2011-11-02
Okay, so I ran a program found through the link in the 3rd post above (boot-repair; [here's the associated log file]("http://paste.ubuntu.com/726887/")), and after that finished, I find myself at a screen like the following:

```



grub>

```

ls doesn't work, otherwise the instructions in the 2nd post, I believe would be adequate.

The commands given (when ```
help
``` is entered) are similar to what is listed on [this page]("http://www.gnu.org/software/grub/manual/grub.html#Command_002dline-and-menu-entry-commands").

How do I see what the location of the device is for the root command in the grub commandline, without ls being available? Or, how do I get into "rescue mode" for the ls command (see [here for documentation]("http://www.gnu.org/software/grub/manual/grub.html#Commands"), though it keeps coming up as an unrecognized command; I'm presuming it is only available in a rescue mode and I'm currently not in it due to that)?

I'm really close to giving up on saving my data and re installing.

---

### Post by tnanek on 2011-11-02
Okay, at the moment I'm re-partitioning the drive in preparation for a new install.

Since I was only using about half of the single hard drive, I'm making that into two partitions, and keeping the data in one, and will use the other for the OS specific files for now... Once I have a functional computer again, I may alter it back to be closer to what it is now... This is presuming the partitioning is successful. If that fails, I'll likely start from scratch.

---

