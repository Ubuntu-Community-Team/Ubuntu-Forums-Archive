---
title: "Lucid Won't Boot, LiveCD won't boot, etc"
date: 2010-06-28
forum: General Help
---

### Post by Jason ON on 2010-06-28
Ubuntu Lucid Lynx 64bit, HP ZV6000

Okay, so I've boon doing a lot of reading on booting problems in 10.04 and it seems as though there are a lot of booting issues after the upgrade or, in my case, out of the blue.

I've only been using Ubuntu for about 6 months now, dual-booting my WinXP box, and for the most part haven't had any issues.  I upgraded to 10.04 via the update manager (or whatever it was that said: there's a new version of Ubuntu out there, please update) sometime in May and never had a problem (although I did choose a wrong setting for the dual boot but that just meant I couldn't get into WinXP).  

Out of the blue one day, after being on the laptop for a few hours I decided to shut down and go outside.  I did the same normal shutdown I always do and shut the computer down.  I came back to it a couple of hours later and it wouldn't boot.  

The HP splash screen pops up (as normal) giving me the opportunity to go into the BIOS if needed and then the GRUB 1.98 loader shows the available versions: Ubuntu kernel, ubuntu kernel and Win partition.  If I choose either of the two Ubuntu kernel's my screen goes blank and I get a flashing curser in the top left corner.  And that's it.  I've let it sit for an hour and nothing.

So, after reading some troubleshooting ideas here at Ubuntu Forums, I tried to boot from my LiveCD (9.10) but the computer will not boot from the LiveCD.

I took out the HDD and slid it into a USB connector and plugged it into another computer and only the WinXP partition shows.  I can't even look into the non-OS partition I created specifically for circumstances like these.

I tried the "GRUB> find /boot/grub/grub.conf" command from the GRUB menu and nothing.  It comes back with a "find is not a valid command" notice.

I have some music and videos on there I'd really rather not lose if I can help it.

Unfortunately, the laptop is too old to boot from a USB (BIOS isn't being updated anymore) and I can't think of any other options.

As far as I know, my only other option is to format the drive and start over.

Any advice is welcome.

---

### Post by wilee-nilee on 2010-06-28
There is a key prompt to chose the boot from device outside of bios, like if you wanted to boot a thumb or cd without changing the bios.

Mine is f12 some are any possible f key or esc, look up on the net your computer model and see if you can find that key prompt.

If you finally get the Ubuntu cd to boot post the bootscript in my signature in code tags as described.

It may be also that you have hardware problems, so you will need to get to the answers on your end to get the script posted for fixing or checking the system overall as to whats on the HD. 

Not every HD is just pluggable into every other computer, and if the MBR is messed up, or grub has been put in the Windows part it wont boot.

Was it a wubi install or a dual boot and what version of Ubuntu was on there?

---

### Post by Pollox on 2010-06-28
I had an issue with blinking cursor when trying to boot the live cd and if I recall correctly something along these lines fixed it:
[http://ubuntuforums.org/showthread.php?p=9308664#post9308664](http://ubuntuforums.org/showthread.php?p=9308664#post9308664)
Although that is for a current install, not the live cd, which is what you want anyway.

As for not being able to read the linux partition on another computer, perhaps you were using something that could not read that type of filesystem?  For instance, Windows can't read ext2/ext3/ext4, and only recent linux distros can read ext4.

---

