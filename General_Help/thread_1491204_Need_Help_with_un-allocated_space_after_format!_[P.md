---
title: "Need Help with un-allocated space after format! [Pic Included]"
date: 2010-05-23
forum: General Help
---

### Post by Elie-M on 2010-05-23
Yesterday I've had enough of the upgrade, I just had to do a brand new format and install for ubuntu 10.04 to get rid of broken and missing and half working packages. So, I reformated on top of my existing ubuntu partition, and when I logged in to the desktop, i found out that my windows partition is now 193 GB (it was 226 GB b4 the format) and there's 34 GB of unallocated and unused waste of HD memory.

I there any way to join those 34 GB of waste back to the Windows Partition? I cannot tolerate such a huge waste of HD memory and I need those 34 GB there... anything I can do about it at all? please help me!

This is the picture I included which should help all understand more what I'm saying..

[http://www.4shared.com/photo/O3EszNjY/HDParts.html](http://www.4shared.com/photo/O3EszNjY/HDParts.html)

---

### Post by louieb on 2010-05-23
What version of Windows? Visa and Win7 - disk management is probably the safest way to go. Right click on my computer>manage> disk management.

XP  -  use Gparted to resize the partition.

---

### Post by Elie-M on 2010-05-23
thanks man that worked, I used extend disk in windows 7 disk managment and regained the space. but a strange thing happened, when I logged in (after windows automatically did a chkdsk) the space was even less than ubuntu saw it (ubuntu 193 GB, on windows 176 GB..) when I extended it, the new space became 210 GB not the original 226 GB.. that's very strange..


Edit: just checked in ubuntu, ubuntu recognizes 226 GB windows partition. Windows only recognize 210 GB. what's a noob OS windows...

---

### Post by jamesisin on 2010-05-23
You may want to mark you thread as SOLVED in Thread Tools above.

---

### Post by Elie-M on 2010-05-23
> **jamesisin said:**
> You may want to mark you thread as SOLVED in Thread Tools above.


I was gonna do it soon, but was waiting if anyone has any final thing to say here doing it

---

