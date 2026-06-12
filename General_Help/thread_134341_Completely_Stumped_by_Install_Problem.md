---
title: "Completely Stumped by Install Problem"
date: 2006-02-21
forum: General Help
---

### Post by bigduke on 2006-02-21
Please excuse me if I'm posting this in the wrong section.

I've installed 5.10 on several computers and really enjoy it.  I never had a problem until I tried installing it on a home-built computer.  This machine has an AMD X2 4200 (dual core), an Asus A8V-MX motherboard, and an ATI 9600 vid card.  Ububtu appears to install uneventfully but then, right after log in, either the X Server completely fails to start or, sometimes, the desktop just appears as a blank brown screen with a cursor.

I spent the better part of a three-day weekend trying to solve this...tried different video cards, no video card, every video driver I could find, Breezy, Dapper, the live CD and even SuSe.  With the live CD I tried every special boot option that looked like even a remote possibility.  Absolutely nothing works.  

I did read that Asus boards are known for not supporting linus well so that might be where I have to leave it and, eventually, just get a different motherboard.

Has anyone had a similar experience? trouble with an A8V-MX or other Asus board? any ideas for a solution?

Thanks

---

### Post by az_human on 2006-02-21
> Then I found out that X was behaving badly, with the text cursor being drawn multiple times in Mozilla & OpenOffice. The fix was to add
Option "ShadowFB" "1"
to the device section of xorg.conf.

Here is the complete thread on getting stuff working on your board, maybe it will help: [http://www.ubuntuforums.org/showthread.php?t=98768]("http://www.ubuntuforums.org/showthread.php?t=98768")

---

### Post by bigduke on 2006-02-21
Thanks

It was just a matter of disabling sound in the bios and then installing a sound card.  I never would have thought of that.  

Dual booting ubuntu and XP Pro and everything seems to work perfectly.

---

