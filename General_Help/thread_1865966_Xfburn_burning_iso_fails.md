---
title: "Xfburn burning iso fails"
date: 2011-10-20
forum: General Help
---

### Post by linuxcss on 2011-10-20
I used to use gnomebaker in ubuntu 11.04 but having installed ubuntu 11.10 and
gnome2 disappearing I switched to xubuntu 11.10 and do not see gnomebaker available for it.

So I am testing Xfburn with xubuntu 11.10 and finding out after readback of a dvd burn that the iso's sha256sums are incorrect and the byte count of the image is wrong, HOWEVER if I burn with wodim it burns correctly.

I need the gui working for others which are not as technical ... any clues why Xfburns fail?
When I specify to burn at 4 speed with Xfburn I still see it reach speeds up to 8x

the difference in size is:
1558491136-1558183936
307200
307200/1024
300 K

anyone have a clue why 300K less would be written using Xfburn then using command line wodim ???
I repeat the test twice with the same results that are wrong.

---

### Post by gsmanners on 2011-10-20
Xfburn does have a serious [blocker bug]("https://bugzilla.xfce.org/show_bug.cgi?id=7705"), so it's weird that it's included in Xubuntu. I guess just remember to avoid using it for now. I always use k3b, myself.

---

### Post by mkendall on 2011-10-20
I'm going to second gsmanner's K3B recommendation. I've had problems with Xfburn for non-iso burning, too. In fact, I don't think I've ever had a successful burn with Xfburn.

---

### Post by linuxcss on 2011-10-20
what other alternatives besides K3b ... since It will bring in a bunch of the KDE environment?

---

### Post by drawkcab on 2011-10-20
Brasero?

---

### Post by ajgreeny on 2011-10-20
Brasero is certainly worth a look now;  It used to be pretty bad at making good burns, and I am another ex-k3b user.  I no longer see the need for k3b as brasero has become so good these days.

---

