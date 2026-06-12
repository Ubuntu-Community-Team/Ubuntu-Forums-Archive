---
title: "Suspend (S3) crashes on Resume"
date: 2009-10-04
forum: General Help
---

### Post by Cuco3 on 2009-10-04
**_System Specs_**
Dual Boot WinXP w/ Jaunty both completely updated
Intel D845PESV Motherboard w/ latest BIOS
Intel Pentium 4 2.4 GHz
GeForce 7600 GS Video Card
WD 80GB JB Hard Drive
Sony DVD/RW Drive
550-Watt Power Supply
PS/2 Keyboard and Mouse

I previously had a problem with S3 Suspend that was attributed to a faulty power supply.

So I bought a new one, replaced it, and now suspend works great ... in Windows XP.

In Ubuntu, it appears to suspend gracefully. But when you go to wake it up, the keyboard is functional for about 3 seconds (pressing num or capslock to test) then it crashes; the screen stays black / blank with the hard drive light on. Pressing Numlock or Capslock doesn't get the lights on the keyboard to change so it's definitely a crash.

I'd love to isolate the culprit, or analyze pm-suspend.log to check for failures, but I'm not sure how to go about that in Ubuntu / Linux.

I will use this thread to track the progress of troubleshooting this problem. Hopefully you guys can offer some of your knowledge and advice, especially with debugging and isolating Suspend culprits.

If none of the above works, I'll then try upgrading to Karmic Koala (9.10). If not, I'm gonna format and try Hardy Heron (8.04).

I appreciate any help and useful links you guys can provide.

---

### Post by Cuco3 on 2009-10-04
please?

---

### Post by Cuco3 on 2009-10-04
> **QIII said:**
> If you have a swap larger than your RAM (by a fair margin -- some people say 2x, but I have always done fine with 1.1x) can you hibernate and wake?

> **Cuco3 said:**
> Hibernate works on XP, but not in Ubuntu. It appears to Hibernate fine (minus the "0000:00:00.0 failed to thaw: error -16" which no one knows what that's about) but on Resume, it goes through the normal process of loading up the GRUB loader, I select the OS, and then the screen stays blank.

I have 1 GB RAM, 1 GB Swap partition.

Well, I deleted both ext 3 partiitons, created a new swap partition of 1.5 GB, and did a fresh install of Ubuntu.

Before I updated anything, tested out Suspend and Hibernate.
Result: Suspend still doesn't work, but now Hibernate does work.
Note: the "failed to thaw: error -16" didn't appear this time when I hibernated.

Then, I installed the latest nVidia drivers (v185) from their website (not through System > Administration > Hardware Drivers)
Result: Suspend still doesn't work, Hibernate still works.
Note: even though the driver was 185, going to "System > Administration > Hardware Drivers" reports it as using the v180 drivers

Next step: *[COLOR=Red]update to Karmic 9.10 (test)[/COLOR]* > [COLOR=SeaGreen]*fresh install 9.04 (test)*[/COLOR] > completely update Ubuntu 9.04 (test) > then install compiz+emerald+cairo deck (test) > install Feisty 7.04 (test) > Upgrade to 7.10 (test) > Upgrade to 8.04 (test) > Upgrade to 8.10 (test)

[COLOR=SeaGreen]Progress[/COLOR]
[COLOR=Red]No Progress[/COLOR]

---

### Post by Cuco3 on 2009-10-04
[SIZE=6][COLOR=Red]*****FIXED*****[/COLOR][/SIZE]
\\:D/ \\:D/ \\:D/ \\:D/ \\:D/ \\:D/ \\:D/ 

Found out the culprit: VIDEO CARD!!!

How:
1. Re-installed Ubuntu, tried hibernate and it worked.
2. Installed the nVidia proprietary drivers, hibernate stopped working with the pci thaw error.

Right there I knew the video card or something with the video card was suspect.

3. Googled "nVidia ubuntu suspend" and came across the following link.

[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

nVidia users experiencing problems with suspend should follow the instructions in this link.

I hope you guys found this info as useful as I have. And now that I officially have Ubuntu the way I want it, I'm ready to rock!!!

:guitar:

---

### Post by Cuco3 on 2009-10-04
MODS!
 
 Please change the title of this thread to [SOLVED] :)

---

