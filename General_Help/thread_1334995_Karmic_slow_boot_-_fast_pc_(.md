---
title: "Karmic slow boot - fast pc :("
date: 2009-11-23
forum: General Help
---

### Post by Nickelrw87 on 2009-11-23
Upgraded to 9.10 from 9.04 - boot times 1:29 says boot chart. ANYONE tell me what the hell is goin on? i see ureadahead takes like 35 secs to do anything...lol i reinstalled ureadahead and everything - lemme know whats up?

[http://yfrog.com/jdoemlaptopkarmic20091122p](http://yfrog.com/jdoemlaptopkarmic20091122p)
[http://img697.imageshack.us/img697/1238/oemlaptopkarmic20091122.png](http://img697.imageshack.us/img697/1238/oemlaptopkarmic20091122.png)


same site diff link

64 bit

---

### Post by DLGandalf on 2009-11-23
same here on i386
Taking 30s for ureadahead to give control to the rest of init processes
for what it's worth, using lvm. Boot time is far beyond 1 minute.

---

### Post by wingnux on 2009-12-14
Really slow boot here too! It used to take me about 30" to boot on 9.04 and now it takes 65" to boot! What a disapointment =/

---

### Post by cormano on 2009-12-14
mine is about 15 seconds from the moment grub takes control. 25 seconds from bios logo. Fresh install here.

---

### Post by skelli928 on 2009-12-28
Yup, same here. 1.25 minutes to boot, where ureadahead takes around 30 sec.

---

### Post by parsim on 2010-01-20
Ditto. Was looking forward to faster boots in 9.10, but it's definitely slower.

From stopwatch:
0:00 Power on
0:26 Complete POST and GRUB
0:32 Black screen, simple Ubuntu logo appears, disk starts working hard
1:31 Screen blanks
1:36 New animated Ubuntu logo appears
1:42 Desktop appears (immediately usable)

Seems crazy that the animated logo takes a minute and a half to appear and vanishes six seconds later.

Bootchart shows 'ureadahead' locking up the disk same as the graphs above, only mine lasts even longer (50 seconds).

---

