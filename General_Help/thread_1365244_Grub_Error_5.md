---
title: "Grub Error 5"
date: 2009-12-27
forum: General Help
---

### Post by Crixler on 2009-12-27
I've got Ubuntu 9.04 and Vista dual booted on my computer, and it's worked great, until now. I just upgraded most of my computer, including the motherboard, and now grub won't load.

It says:
"GRUB Loading stage1.5.


GRUB loading, please wait...
Error 5
_"

How do I fix this, so Grub will load properly?


Also, if anyone's about to point out that Vista won't work after a motherboard change, I understand this and intend to do a fresh install of Windows 7 on an additional hard drive I also added once I get a copy (in about a week or so.)

Would formatting my Linux drive and installing 9.10 get everything working, or would that be a bad idea?
I'm rather new to Linux (as well as motherboard upgrades), so this is a new experience for me.

Thanks!

-Crixler

---

### Post by gordintoronto on 2009-12-27
First, make sure you have full backup of all your data!

Then install from scratch, the same as you would for a brand new computer.

---

### Post by Crixler on 2009-12-27
You're talking about reinstalling Linux, right, not Windows?
If that's the case, I don't even need to bother backing things up, all I really did was modify the interface to resemble Windows, which I can just do again.

Thanks for the help!
The reply came faster than I had expected.

---

### Post by Crixler on 2009-12-27
Ok, so I reformatted my Linux hard drive and installed 9.10 over it, and now it's giving me error 22. :(

What went wrong?

Edit: Upon briefly googling error 22, I read something about switching to Linux hard drive to the primary one in the bios, so I did that, and now it says:
"Verifying DMI Pool Data .........
Boot from CD/DVD :
GRUB _"

and the _ keeps blinking and it's just sitting there. Would I need to set it as the master with jumpers as well? it's currently slaved to another hard drive.

Edit 2: I switched the hard drives back to the way they were in the Bios, and it's giving me error 22 again.

---

### Post by asqn34 on 2009-12-27
hi there

grub error explaination:

[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

in your bios, the first device should be the HDD with linux (master) and windows (slave)

As you installed linux After windows, your Grub will be your default bootloader.

---

### Post by Crixler on 2009-12-27
I just got it working after following these directions: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) !
Thanks for helping out!

---

