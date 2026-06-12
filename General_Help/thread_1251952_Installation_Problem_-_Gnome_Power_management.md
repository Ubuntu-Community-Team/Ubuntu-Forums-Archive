---
title: "Installation Problem - Gnome Power management"
date: 2009-08-28
forum: General Help
---

### Post by turf on 2009-08-28
```

Installation Problem
the configuration default for Gnome Power management have not been installed correctly.

```this is the message after booting up..
what shall ido to correct this?
and what does DRDY means?

---

### Post by mike555 on 2009-08-28
If you installed to an older computer perhaps the bios doesn't support the power management , just a thought.

---

### Post by turf on 2009-08-28
yes this is a very old pc. but this works good. infact ubuntu works fast inside this pc.
its just that it gives me this error.

---

### Post by drink_stir on 2009-12-27
im having the same problem. and it wont let me boot into ubuntu. and mine is installed on a newer hp pavillion laptop. idk what the bios is. im thinking its pheonix. i have no idea how to fix it. it only happens when i restart on battery. but once it hapens i cant get around it. im pretty new to linux.

---

### Post by RCepeda on 2009-12-28
I am having the same problem. I just walking in this morning and now I can't get in. Is there anything I can do?

---

### Post by RCepeda on 2009-12-28
My problem was from Simple Backup. It created a file that took up the rest of my HD and would not allow my system to log in. I used this to find the file.

sudo find / -name '*' -size +1G

---

### Post by drink_stir on 2010-02-25
all i had to do to alleviate the problem what just update. now everything works fine and never had a problem since. oh... i got rid of that pesky dual boot setup to. dont know if that had anything to do with it but when i got rid of windows it never happened again. and it was a while till i could do all the updates after the install.

---

