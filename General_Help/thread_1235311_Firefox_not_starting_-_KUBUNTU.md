---
title: "Firefox not starting - KUBUNTU"
date: 2009-08-08
forum: General Help
---

### Post by foska on 2009-08-08
I am using KUBUNTU 9.04.  I have managed to install Firefox 3.5 and it works well generally but I am finding that when I close firefox and try to restart it again I get a dialog box saying that "Firefox is already running. To open a new window......., or restart your system"  (see file attached for full text). To resolve this I have to use the System monitor and "kill" the Firefox process that is running (that I already closed).  I find that I get this problem if I close the browser with several tabs open.

Does anyone know how to resolve this issue? If so how can I get it resolved on my system?

Thanks in advance for your help.

PS I have attached screenshots

---

### Post by lovinglinux on 2009-08-09
I have the same issue sometimes, but I don't know what is causing this on my system. I couldn't find a way to solve this yet.

I'm running a compiled version of Firefox 3.5.1.

---

### Post by Raffles10 on 2009-08-09
This is due to a conflict with 'gtk-qt-engine', it's been discussed over at the arch forums. I don't think there's a permanent fix but you could delete the 'lock' file from ~/.mozilla.

---

### Post by sleepitoff on 2009-08-10
I'm really sick of this problem! Everytime!

---

### Post by hibliss on 2009-08-10
> **sleepitoff said:**
> I'm really sick of this problem! Everytime!

It is fixed in the latest Nightly Neon build of KDE.

---

### Post by sleepitoff on 2009-08-10
Hmmm... I love FireFox, but is it safe to install a nightly build of KDE just for this fix? :confused: 

I'll just use Chromium until it gets fixed. 

I tried removing the 'lock' file as well and that didn't help.

---

### Post by Rob_H on 2009-08-10
I'm using Firefox 3.5 (Shiretoko) on three different Kubuntu systems and I have not seen this problem. I did upgrade to KDE 4.2.4 back when it became available, so maybe that makes a difference. You could try upgrading to that rather than a nightly.

I have noticed it on rare occasions when I try to restart Firefox immediately after closing it, but if I wait a few seconds and try again, it's fine. Don't think that has anything to do with KDE.

---

### Post by sleepitoff on 2009-08-10
Yeah, upgrading from 4.2.2 to 4.2.4 fixed it. 

I have unsupported updates and pre-released updates checked in synaptic, so I would have thought I was on latest, but I guess not. 

[http://ubuntumanual.org/posts/178/install-or-upgrade-to-kde-4-2-4-in-ubuntu-or-kubuntu](http://ubuntumanual.org/posts/178/install-or-upgrade-to-kde-4-2-4-in-ubuntu-or-kubuntu) 

Thanks

---

### Post by foska on 2009-08-11
This did not solve it for me :sad:

---

