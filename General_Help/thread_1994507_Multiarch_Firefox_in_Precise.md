---
title: "Multiarch Firefox in Precise"
date: 2012-06-02
forum: General Help
---

### Post by Helkaluin on 2012-06-02
Hi all,

I'm trying to utilise APT's Multiarch support to install and run a 32-bit version of Firefox in an otherwise 64-bit Linux setup for the reason of lowering memory use.

So far everything's going fine, except that globalmenu doesn't work because I can't quite seems to be able to install the packages appmenu-gtk and appmenu-gtk:i386 at the same time.

Is Multiarch still not fully-implemented yet?

---

### Post by Paddy Landau on 2012-06-03
I don't know that this is fully supported in Ubuntu.

If you have low memory, perhaps the best thing is to move to [Lubuntu]("http://lubuntu.net/"), an official Ubuntu variant for older, slower or reduced-spec hardware.

Otherwise you may be stuck with having to use 64-bit Firefox.

---

### Post by Helkaluin on 2012-06-04
Problem solved.  32-bit version of appmenu-gtk is not needed.

Downloaded official Mozilla build for Linux i386, extracted tarball in ~/bin/firefox-stable-i386/, symlinked firefox executable into ~/bin/.  Downloaded 32-bit deb of firefox-globalmenu with "$ apt-get download firefox-globalmenu:i386", extracted relevant plugin folder, symlinked into ~/.mozilla/profile/extensions/.  Installed relevant 32-bit versions of dbusmenu libs with multiarch successfully.

---

### Post by Paddy Landau on 2012-06-04
Excellent, I'm glad you managed to figure it out.

Has it lowered memory usage?

---

### Post by Helkaluin on 2012-06-05
It has, quite considerably.

---

