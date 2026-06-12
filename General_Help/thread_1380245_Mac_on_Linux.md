---
title: "Mac on Linux?"
date: 2010-01-13
forum: General Help
---

### Post by ooloo on 2010-01-13
Hi, 

Basically, the story is a while back I was given an old Mac OS X disc from a friend and when I was given this, I read up about setting it up in Virtual Box OSE or something but apparently, I was unable to do that, I tried still, just in case and was not so I found it again today whilst looking around and was wondering what to do with it and then I thought of looking to find a Mac compatibility layer like Wine but for Linux.

Does anybody know if there is one? I have found on Google Mac-On-Linux and PearPC but I'm unsure about them. Especially the MOL thing since the latest news was from 2007 and PearPC because I don't really get what it is.

I was wondering if somebody here know of anything that can help me either install this disc to a virtual machine with VirtualBox OSE or if there is a Mac compatibility layer anywhere around like Wine.

I have Ubuntu 9.10 with something over 2Ghz Intel processor and just under 1GB of RAM but I've been able to run other systems in a VM so maybe I can run Mac OS X with that. I use an ATI display driver too, if that helps.

---

### Post by warfacegod on 2010-01-13
The only thing I can think of that sounds like that is mac4lin.

---

### Post by wiebeest on 2010-01-13
> **warfacegod said:**
> The only thing I can think of that sounds like that is mac4lin.

Appearence-wise Mac4Lin and such themes combined with a dock of choice, be it Cairo-dock, AWN, and what have you got, is the path of choice. Combined it gives your Ubuntu distribution a pretty good OSX-ish appearence.

Then you've got emulators, from which Bassalisk bears to mind, but that only gives you retro OS 7. OSX can be emulated through PearPC, but that is PowerPC emulation of OSX Tiger on an x86 pc which is, well, ssssslllloooowww.

Otherwise there's the OSX86 scene which does give you native OSX Leopard on your x86 processor running astonishing well. But it involves the usage of hacks and therefore you should seek knowledge elsewhere and not here on Ubuntu-forums.

---

### Post by sword_king on 2010-03-02
Mac4Lin is a theme for Gnome that looks and tries to act 'Macish', but won't let you use your Mac disk, so the above poster was, to say the least, inattentive and uninformed, but felt compelled to answer, anyway. Pay no attention.

PearPC emulates a New World (G3 & later) PowerPC, and runs OSX. Sheepshaver emulates an earlier PPC, and runs OS8.1-OS9.04.  Basilisk emulates earlier Macs, using System 6.0 - OS 8.1.  All have certain limitations.  IIRC, they all run on both x86 (Win9x & later, BeOS, and Linux) and PPC (MacOS, BeOS, Amiga, and Linux) architecture. One of these, depending on which Mac OS disk you have, is probably going to be your best choice.

AFAIK, VirtualBox only emulates x86 and AMD64/Intel64 hardware, so it may be able to emulate an IntelMac, I don't know.  If you want to try it, it's free for private use from <virtualbox.org>, and newer than what's in the repositories.  I know it'll emulate an x86 on an Intel Mac (to use Linux or Windows, for example), but I don't know about the other way around, which is what you're looking for.

Mac-On-Linux runs Mac OS natively (not emulation) in a window or full screen in **Linux for PPC**.  When it works it works wonderfully, but like so many things about Linux, when it doesn't it is exasperating!  I run 3 G3 iMacs, an eMac, and a BeigeG3 with Xubuntu for PPC, and am trying to get MOL running, which is why I came across this thread.

HTH, SK

---

