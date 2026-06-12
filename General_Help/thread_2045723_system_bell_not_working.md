---
title: "system bell not working"
date: 2012-08-21
forum: General Help
---

### Post by thomsmells on 2012-08-21
I'm trying to make a simple bash script that uses the system bell, but it's not working.

It was muted and set to 0 in alsamixer, and have now unmuted it, but still it won't make any noise.

Any clues?

---

### Post by thomsmells on 2012-08-22
Update: The actual system bell is working (the low battery alarm sounded), but the command ```
echo -e "\a"
``` does nothing but print a newline.

---

### Post by marinara on 2012-08-22
system bell is diabled in lubuntu.  you can run the "beep" command if you have the pcspkr module loaded.

---

### Post by abyrne on 2012-08-22
Just to clarify, run
```
sudo modprobe pcspkr
```
but that will only keep the speaker on until next reboot. You'll have to delete the 'blacklist pcspkr' line in /etc/modprobe.d/blacklist if you want to enable it permanently.

---

