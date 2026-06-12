---
title: "Cloning system"
date: 2010-02-28
forum: General Help
---

### Post by allsaythat on 2010-02-28
Hi,
I'm running Ubuntu 9.10 but quite heavily customised, both in appearance and programs. Is there some way I could clone my system's programs and system settings, as well as files onto another computer rather than have to customise it all over again?
This would be from a laptop to an empty desktop.
Thanks.

---

### Post by mike555 on 2010-02-28
ReMastersys will do that ........... just make sure you don't have too much stuff in your home folder (like movies)or it won't fit on a dvd .    when done you should have an installable dvd with your settings .......

-- or hook the new harddrive on a usb adapter cord , and use clonezilla.

---

### Post by spikyjt on 2010-02-28
Or boot both systems up with [SystemRescueCD]("http://www.sysresccd.org/") and clone the disk over the network. Or if you feel like ripping the disk out of the laptop and shoving it in the desktop, you can do it on the same machine with partclone (which comes with sysresccd). Or you could plug the desktop disk into the laptop with a USB harddisk adapter if you don't want to rip the laptop apart. The desktop will boot happily, like a new install and load the correct drivers. You might just want to change the hostname, by editing /etc/hostname and rebooting.

---

### Post by asmoore82 on 2010-02-28
Clonezilla's Live CD's ~ [http://clonezilla.org/](http://clonezilla.org/)

I hate to use this analogy, but think of it as "Norton Ghost" for linux.
It can save/restore/clone Windows/Linux/Multi-boot setups.

---

### Post by allsaythat on 2010-03-01
Excellent. I'll give it a shot. Thank-you.

---

