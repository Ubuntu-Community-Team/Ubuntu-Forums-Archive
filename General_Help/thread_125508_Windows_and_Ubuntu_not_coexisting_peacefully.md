---
title: "Windows and Ubuntu not coexisting peacefully"
date: 2006-02-04
forum: General Help
---

### Post by neolithic on 2006-02-04
Greetings,

I recently reformatted and partitioned my 80gb laptop hdd into a 50gb and 30gb pieces.  I have Windows XP installed on the 50gb portion and Ubuntu 5.1.0 on the other.  I installed XP first and verified that everything was working as it should.  After installing a Ubuntu I have run into a few issues that I can't figure out, mainly dealing with USB devices attached to my laptop.  My external sound card (Creative Extigy) was behaving oddly under Ubuntu (little to no sound output even though it was recognized) until I rebooted, but now it seems to work fine.  XP however will not put any sound out through it since installing Ubuntu.  It too says its recognized and installed, but no sound is produced (I have checked all the painfully obvious things like volume control and device manager).  Also, everytime I boot from Linux to XP my system clock is messed up (I'm assuming this is because it uses GMT and converts it?).  That is a minor inconvienence but if I could fix it I would like to.  Lastly, how can I edit GRUB to make XP the primary boot OS?  Thanks in advance for any help.

---

### Post by alamba on 2006-02-04
Edit grub:
vi /boot/grub/menu.lst

Try setting the location on your ubuntu. That might fix the clock issue.

A

---

### Post by neolithic on 2006-02-04
Any ideas on the sound issues

---

### Post by Fallen Guru on 2006-02-04
Can't help you with the sound but the clock issue is due to ubuntu assuming UTC in the system clock. It really should ask at install time, like the Debian installer does.

in /etc/default/rcS should be a line like

RTC_IS_UTC=yes

just change that to no. Location and variable name probably slightly different, I'm on XP right now.

---

### Post by handy on 2006-02-04
It does ask at install time!

---

