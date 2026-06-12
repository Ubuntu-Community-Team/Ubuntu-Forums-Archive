---
title: "Suspend OK hibernate not! (9.10)"
date: 2009-11-16
forum: General Help
---

### Post by cashtr on 2009-11-16
Hi all,

I have just installed Ubuntu 9.10 on my Toshiba laptop and have a bunch of problems. I don't know if I shoul asked them in one thread or separate them, so here goes: 

1) I can suspend and wake the laptop with no problems but when I try to hibernate I get an error saying "ata2 drive not ready, soft reset failed" and the same message with ata3. 

2) Power management is not working. For example, I set it to suspend when the lid is closed, or dim the screen brightness when on battery and it does none of these things. Additionally, after working around 30 min, fans start working at full speed and never stop although the laptop is very cool.  

Thanks for your time.

---

### Post by P4man on 2009-11-17
to hibernate you need a swap partition that is large enough. Do you have one?

As for the other problems, it might help if you gave the exact model of your machine. but already I would suggest checking if there is a newer bios for it, as it sounds acpi related.

---

### Post by cashtr on 2009-11-17
I changed the swap partition to a larger one (10gb for 3 gb RAM) but the problem persists. The behavior changed a little though. Now if I run gparted it shows the swap space but it is in swapoff mode. Hibernate leads to a blank screen with cursor, when I move the cursor the login window appears and I can continue from where I left off. If I change to swap on from gparted, it turns back to the same ata2 soft reset failed error.

For the bios I found a recent Bios update and flashed the bios, however, it did not help with the acpi problems. The machine is a Toshiba Satellite L505D-S5965.

---

### Post by P4man on 2009-11-18
Not sure.. have a look here:
[http://ubuntuforums.org/showthread.php?t=1301101](http://ubuntuforums.org/showthread.php?t=1301101)

Lots of problems with that laptop. Perhaps file a bug report.

---

### Post by cashtr on 2009-11-18
Thanks for the help. I guess I will wait for the next ubuntu release to try to swith to linux.

---

### Post by acarlstein on 2009-11-30
I have a HP G50, and a Gateway 7510GX.

With Ubuntu 9.04, I had problems with the hibernation mode but it was easily fixed by increasing the SWAP partition to a size bigger than the memory ram.

They were working like a Sweden Clock. Perfect!

Until I update to 9.10, then everything went to hell.

In both Gateway and HP, the hibernation mode doesn't work.

Both computers completely freeze sometimes (which is the equivalent to the blue screen of MICRO$OFT).

Also, in the gateway, my ATI card stop supporting 3D.

Are we imitating MICRO$OFT? Are we pushing users to buy new hardware? Are we using the users as beta testers against their will? What is going on?

If is working don't fix it. And if you want to experiment then instead to publish 9.10, use 9.09 so we know that is untested and may be buggy to hell.

---

