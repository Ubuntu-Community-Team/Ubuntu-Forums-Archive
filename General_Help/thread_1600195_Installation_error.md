---
title: "Installation error"
date: 2010-10-18
forum: General Help
---

### Post by Darbeezeh on 2010-10-18
Whenever I run wubi to install Ubunutu I get the following error:  pyrun.exe - No Disk There is no disk in the drive.  Please insert a disk into drive \Device\HArddisk2\DR17.  When I click any of the three buttons on the bottom &quot;Cancel, Try Again, Continue&quot; it changes the DR17 to DR18 and back and forth.  Help please.

---

### Post by bcbc on 2010-10-18
unplug external devices e.g. sd cards, phones, ipod, multi-card readers etc.

python (or some code in wubi) has a problem when it iterates through the disk 'devices' and it does this a lot - so it looks like a loop, but it's not. If you kept hitting Continue it will eventually work, but it's a pain.

---

### Post by Darbeezeh on 2010-10-18
> **bcbc said:**
> unplug external devices e.g. sd cards, phones, ipod, multi-card readers etc.

python (or some code in wubi) has a problem when it iterates through the disk 'devices' and it does this a lot - so it looks like a loop, but it's not. If you kept hitting Continue it will eventually work, but it's a pain.
This did the trick, thanks a ton.

---

