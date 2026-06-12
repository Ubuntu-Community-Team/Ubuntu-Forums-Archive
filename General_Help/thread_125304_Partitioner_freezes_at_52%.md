---
title: "Partitioner freezes at 52%"
date: 2006-02-03
forum: General Help
---

### Post by yashoda on 2006-02-03
Hi,

I'm totally new to Ubuntu, and am really sick of MS xp...

I've got my Ubuntu CD pack, and tried 2 separate new install cds, and it gets stuck at 52% on the partitioner.

I've pressed Ctr alt f3, it says /dev/hda" failed (input/output)

Please advise me how to proceed (with detail, non-jargon instructions please).

Thank You VERY much!

ys,
yashoda

---

### Post by aysiu on 2006-02-03
Either you're experiencing a hardware failure, or the CDs you got shipped are corrupted (yes, even the official ShipIt CDs can be).

---

### Post by yashoda on 2006-02-03
Hi Aysiu, 

Thanx for replying!

XP and the Ubuntu Live CD work fine though.

I have no problems otherwise with the computer.

I've seen a few others have had problems with the partitioner getting stuck on 52%, but with no real solutions.

anyways... still hoping to be microsoft-FREE.

Ys,
yashoda

---

### Post by aysiu on 2006-02-03
[QUOTE=yashoda]
XP and the Ubuntu Live CD work fine though.[/QUOTE] This rules out the hardware failure, but I still think the installer CDs could somehow be corrupted. Do you have the ability to get a new one fast (broadband internet connection and a CD burner)?

---

### Post by yashoda on 2006-02-03
Hey Aysiu,

thanx again!

really appreciate it.

well, I've tried 5 different Install CDs, and these have worked on other computers, just not on this one (I'm installing on my wife's old thingie).

they've all worked fine before.

I've even tried a new one from a downloaded iso.  same problem.

Ys,
yashoda

---

### Post by aysiu on 2006-02-03
Yikes. I don't know what to tell you then. Do you happen to have two CD-ROM drives? Maybe you could try the other one?

---

### Post by yashoda on 2006-02-03
Yet again...

thanx! :) 

Yup, I've tried using the other CD-ROM drive.  Niks... nothing.

Ys,
yashoda

---

### Post by Stereotypical Rage on 2006-02-03
I think this has to deal with LBA and Auto in the BIOS, don't quote me on that.

---

### Post by TechSonic on 2006-02-03
Go into Bios and reset to optimized defaults.
Do not edit anything!  Just reset, save, exit, install.

The reset will REdetect your hard drive.  Also, your hard drive may have errors on it (Bad sectors).  Windows installer works fine over this because it just installs around the bad spots and reports the drive is smaller then it is.  Linux on the other hand, doesn't.  My suggestion is to purchase a new drive or take back the one you have if still under warrenty.

---

