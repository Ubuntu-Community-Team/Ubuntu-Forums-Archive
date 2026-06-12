---
title: "Ubuntu 9.04, 9.10a3 unusable on my laptop"
date: 2009-08-05
forum: General Help
---

### Post by Aleksei Vasiliev on 2009-08-05
Since Ubuntu 9.04, I cannot use any version of Ubuntu on my laptop (Sager NP2092/Compal JFL92). It will install, but it will constantly pause until I tap my touchpad or hit a key. Any text cursor will stop blinking, any download will stop, my wi-fi will drop until I give it input.
This happens with ext4 or ext3, 9.04 or 9.10a3, AHCI enabled or disabled. All x64 since I have 4GB of RAM.
Tried disabling all power-management in 9.10a3: Disabled acpi-support, acpid, and the gnome power manager. Still occurs.

Does anybody have any idea what could be happening?

---

### Post by Aleksei Vasiliev on 2009-08-05
I will bump this eternally.

---

### Post by Aleksei Vasiliev on 2009-08-07
I have mild hopes that this will be fixing in KKK 9.10. Actually I just wanted to use that acronym. I think I'll try using Xubuntu, though, and see what happens. And then try Ubuntu x86.

---

### Post by Aleksei Vasiliev on 2009-08-07
Xubuntu 9.04 AMD64, bug shows in installer.
Ubunt 9.04 x86, bug shows in installer.
Next: Ubuntu 8.10 AMD64.

---

### Post by Aleksei Vasiliev on 2009-08-07
8.10 AMD64 does not work either. Although I left it alone and it did go to the next page after about 10 minutes of no actions at all.

---

### Post by Aleksei Vasiliev on 2009-08-07
Bug appears in Ubuntu 8.04 with full updates and a custom kernel.
Bug appears in Debian 5.02 installer.

---

### Post by Aleksei Vasiliev on 2009-08-10
130 views and no ideas at all on how to fix this. Awesome.

---

### Post by wojox on 2009-08-10
If you didn't tag the thread Linux sucks, you would probably get more help.

---

### Post by P4man on 2009-08-10
Other ppl seem to have no such issue with the same laptop. are you sure its not a hardware issue? Have you at least tried updating your bios?

---

### Post by Aleksei Vasiliev on 2009-08-10
> **wojox said:**
> If you didn't tag the thread Linux sucks, you would probably get more help.If it was working I wouldn't have tagged it that. I've gone off a few previous suggestions I'd received from Linux users and devs and nothing helped. I'd say Windows sucked if it refused to run on a modern laptop, too.

> **P4man said:**
> Other ppl seem to have no such issue with the same laptop. are you sure its not a hardware issue? Have you at least tried updating your bios?Running the latest BIOS, 1.18. No idea how to tell if it's a hardware issue.

---

### Post by P4man on 2009-08-10
> **Aleksei Vasiliev said:**
> . I'd say Windows sucked if it refused to run on a modern laptop, too.

You could also say your laptop sucks, because its unable to run a modern OS ;)

Anyway, you tried every possible ubuntu with no result; I'd try something completely different like knoppix or pclinuxos or something very much non debian and with an older older kernel, or heck even windows, just to see if its possibly a hardware issue or not.

---

### Post by lisati on 2009-08-10
> **Aleksei Vasiliev said:**
> If it was working I wouldn't have tagged it that.
I read [this thread]("http://ubuntuforums.org/showthread.php?p=7512589#post7512589"). Don't forget that ext4 is still a relatively new kid on the block.......

---

### Post by Aleksei Vasiliev on 2009-08-14
> **P4man said:**
> You could also say your laptop sucks, because its unable to run a modern OS ;)

Anyway, you tried every possible ubuntu with no result; I'd try something completely different like knoppix or pclinuxos or something very much non debian and with an older older kernel, or heck even windows, just to see if its possibly a hardware issue or not.

Windows 7 beta runs with very few issues. I'll work on finding something non-Debian to try. It won't be Arch Linux seeing as how when I tried to install it it gave me two fatal errors and corrupted my GRUB.

This did remind me that I do have an occasional strange problem which I attempted to fix using the BIOS update, but it didn't. Sometimes when I log back in from the Windows lock screen, my keyboard turns off completely. I have to either restart, hibernate or drop the computer into a lower power-state (make it go to Standby) and then it will be fixed.


> **lisati said:**
> I read [this thread]("http://ubuntuforums.org/showthread.php?p=7512589#post7512589"). Don't forget that ext4 is still a relatively new kid on the block.......Yeah, but I tried using ext3 too. And the installer of Ubuntu exhibits the same strange "pausing" bug, and I don't think it uses ext4.

---

### Post by P4man on 2009-08-14
> **Aleksei Vasiliev said:**
> 
This did remind me that I do have an occasional strange problem which I attempted to fix using the BIOS update, but it didn't. Sometimes when I log back in from the Windows lock screen, my keyboard turns off completely. I have to either restart, hibernate or drop the computer into a lower power-state (make it go to Standby) and then it will be fixed

Aha!
Well, there you go, its almost certainly a problem with the machine then. You can try 576 linux distro's , but if its not a hardware failure, then at least Id guess you got a corrupted bios. Check your manual if there is a way to reset it. Often involves removing a battery and shorting two pins, but it should be explained in the manual. If there is no reset bios option, try flashing it again with the latest bios. Or even an older one.

---

### Post by Aleksei Vasiliev on 2009-08-21
I've re-flashed my BIOS and the problem still happens. Noticed it this time with the Inquisitor live CD I was trying to run.

Memtest86+ does not have any problems running and also doesn't detect any problems with my RAM, so that's fine at least.

My laptop is out of warranty so I can't get it repaired, though I did just e-mail support.

---

### Post by HandeH on 2009-08-22
I'm also affected by this strange pausing (2 week old Compal JFL92 with Jaunty). Also the mics (soundcard is Realtek ALC268, more at this
[forum topic]("http://ubuntuforums.org/showthread.php?t=551615&highlight=alc268&page=4&nojs=1")) do not work (only extremely low volume level when playing speech recorded with gnome-sound-recorder 2.26.0). BIOS (the newest 1.18 ) HDD and start up passwords are set. Auto login enabled. 

Also the WLAN card (Intel PRO/Wireless 4965AGN) is unstable (more at [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/313854"))

Edit 12-05-2011: There is still some sound problems (quality of recording through microphones), but otherwise the laptop is working great.

---

### Post by bluebledthesea on 2010-01-19
I have this same exact problem on a Sager NP2092 with Ubuntu 9.10 and BIOS version 1.18. Has anyone found an actual solution to this? I see the "clocksource=jiffies" suggestion but I'm not yet experienced enough to know how to implement it, plus, it looks like a bandage and not an actual fix to me. Thanks.

---

