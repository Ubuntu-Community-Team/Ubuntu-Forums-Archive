---
title: "Can't update from Jaunty/2.6.30"
date: 2010-02-07
forum: General Help
---

### Post by Praxicoide on 2010-02-07
Hi, I have a pretty old Sony lapto where I Installed Ubuntu minimal + xfce on it. So far it has worked great. The only problem is that I cannot update to Karmic. Back when it was released, and after a few days of headaches, I resigned myself to continue using Jaunty and wait for Lucid. However, recently, not being able to update webkit past a certain point (because of glib dependencies) is causing me some issues.

To explain the problem: regardless of boot options, any Karmic live CD will always freeze during boot-up, stating: "error machine check" and "atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly." Despite what it says, this is NOT a hardware problem, because I can run the computer just fine under Jaunty.

I've tried compiling the latest kernel under Jaunty (to see if I could upgrade this way instead) and no luck, kernel debs or compiles work only as far as 2.6.30, but installing either 2.6.31, 2.6.32 or even the 2.6.33-rc will result in the same kernel panic as with the live CD. I even tried to install a Karmic kernel with backports modules installed without success.

By the looks of it, I won't be able to install Lucid in this machine either, which is frustrating. I've tried reading about the changes made to 2.6.31 to find out why this laptopl can't boot into it,but so far I haven't been able to find anything. A possibility is the ATI Radeon modesetting introduced in this kernel. This computer has an ATI Rage graphic cards. Would the modesetting apply to it too? Maybe this is what causes the kernel panic?

Any tips would be more than appreciated.

---

### Post by Praxicoide on 2010-02-22
I tried Arch Linux out of desperation, but it doesn't look too promising. I get a bunch of errors during the image bootup, and while I can get to the terminal, the network never starts up, making me unwilling to try to install it.

The cd does come with a LILO Diagnostic, and from that I get a number of errors:

"Boot reported from DX = 0x0002 (boot device is 0x02 in DL)
It looks like the BIOS failed to report the boot device in DL."

Extended memory blocks: A different amount of memory is reported by this function

Get Disk Type (device 01h): BIOS eror code = 0x01 (invalid command)

and the same message for Drive parameters."


Are those things significant when I can successfully run the 2.6.29 kernel?


OK, this is weird, now I get kernel panic when booting, even though nothing is changed...


EDIT:

My normal Jaunty boot always states:

"Host SMBUS Controller not enabled! - upgrade BIOS or use force=1"

I looked into updating the BIOS, but the Phoenixbios Update Utility available at Sony's site is for Windows only. Can I used it under wine, or is there another way to do this?

---

