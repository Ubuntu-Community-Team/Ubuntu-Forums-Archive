---
title: "Module &amp; daemon blacklist?"
date: 2006-06-09
forum: General Help
---

### Post by norman_ on 2006-06-09
Hi everyone. I'm new here, installed xubuntu 2 days ago and am very happy with the whole package. Easy to use, good lookin and overall very pleasant experience.

Now I would appreciate answers to 2 short answers:

1- How to you blacklist a module so that it doesn't load automatically on startup? (ehci_hcd conflicts with something and prevents my ipod from being detected automatically. I don't want to have to modprobe -r it every session). 

2- The BootUp Manager doesn't seem to work for me. I uncheck the processes I don't want and they come back. I don't need all that laptop crap :p  Is there a text file somewhere I can edit to choose which daemon/processes get launched at startup? In archlinux, it used to be in rc.conf but I am not familiar with Debian/Ubuntu file structure.

I would be very grateful if you guys/gals could help me deal with these 2 minor issues. 

Thanx a lot for your time

Norm

---

### Post by 23meg on 2006-06-09
> 1- How to you blacklist a module so that it doesn't load automatically on startup? (ehci_hcd conflicts with something and prevents my ipod from being detected automatically. I don't want to have to modprobe -r it every session). 
Add its name to the /etc/modprobe.d/blacklist file.

---

### Post by norman_ on 2006-06-09
That was really quick! Thanks a lot, now I feel a bit stupid as the path and filename are pretty self explanatory.

---

### Post by norman_ on 2006-06-09
SOLVED

BUM started working after reboot. Thanx

---

### Post by 23meg on 2006-06-09
Glad it helped you. For more info on the init.d structure check this out:

[http://www.debian.org/doc/debian-policy/ch-opersys.html](http://www.debian.org/doc/debian-policy/ch-opersys.html)

---

