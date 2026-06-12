---
title: "Need help to fix ubuntu 9.10  black screen"
date: 2010-04-23
forum: General Help
---

### Post by tehno 2 on 2010-04-23
Hello there,

Can some one help me please to solve this issue, Ubuntu works normally and then it switches to a black screen and nothing works after that. not even Ctrl/Alt + Del.
it does not happen at a certain point, sometimes it happens right after good reboot and some other times it happens after 30 to 40 minutes and some other times it does not happen.
This is driving me crazy for I had to un-install and re-install twice for the same reason and I could not find a solution at all.
My UBUNTU IS INSTALLED WITHIN WINDOWS/ DUAL BOOT
Thanks in advance

---

### Post by klemes on 2010-04-24
I had similar problems in a Karmic installation with an Intel 945GM videocard.Never found a complete solution other than it helped a little to have an xorg.conf file with the vertical & horizontial frequency of the monitor and to turn off completely compiz effects.The later took care of the freezing after getting in the desktop problem but did nothing for the blank screen at bootup problem.What I also did was to install the latest intel driver from xorg-edgers.
Anyway in an almost identically-speced machine running now Ubuntu 10.4 Lucid Lynx RC I never had similar problems which means that both of these issues have been fixed(at last :) )in the new version.:P

---

### Post by tehno 2 on 2010-04-25
> **klemes said:**
> I had similar problems in a Karmic installation with an Intel 945GM videocard.Never found a complete solution other than it helped a little to have an xorg.conf file with the vertical & horizontial frequency of the monitor and to turn off completely compiz effects.The later took care of the freezing after getting in the desktop problem but did nothing for the blank screen at bootup problem.What I also did was to install the latest intel driver from xorg-edgers.
Anyway in an almost identically-speced machine running now Ubuntu 10.4 Lucid Lynx RC I never had similar problems which means that both of these issues have been fixed(at last :) )in the new version.:P

Well, thank you man, could not fix the 9.10 and the upgrade did not work it took for ever doing the install and got stuck at certain:guitar: point and did not any further. I removed the 9.10, downloaded 10.04  ISO and installed it.
it is really wonderful and much easier to handle updates, downloads, drivers and every thing.
"Thanks again

---

### Post by dino99 on 2010-04-25
that sound as a power saving problem: check bios settings first then ubuntu powersaving

remove screensaver if activated and hibernation too

then : sudo dpkg --configure -a

---

### Post by klemes on 2010-04-25
Believe me I had tried everything including uninstalling the Xscreensaver & the power-manager but the problem persisted and in fact persists to this day albeit a lot more sparingly.I did not upgrade this particular computer because it does not belong to me and has important files in a xp partition and I was intimidated by (the largely unknown to me )Grub2 inevitable upgrade and a possible implications of an non-booting xp installation which is the owner of the computer's main OS.....:(
:guitar:

---

