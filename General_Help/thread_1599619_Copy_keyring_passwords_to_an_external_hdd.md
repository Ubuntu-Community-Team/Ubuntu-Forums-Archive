---
title: "Copy keyring passwords to an external hdd"
date: 2010-10-18
forum: General Help
---

### Post by Hobbsilla on 2010-10-18
Is there any way to copy saved passwords for websites and WiFi networks onto a harddrive by finding some sort of file(s) in a given directory? I want to update to 10.10 by doing a fresh install but would like to transfer my passwords easily.

---

### Post by robsoles on 2010-10-18
If you copy /home to a backup drive (or have it on it's own partition   and not encrypted individual homes) then you should be able to install   10.10 right around it (or copy it back after), just use the same   username and, perhaps for paranoia sake, same password for your account   as you last had in 10.04 using that /home folder.

I can re-install the same version over my system with barely a  forethought of manually partitioning and preserving my /home. Just  having /home on it's own partition is a blessing - I  make a smallish  partition (~30Gb) for the / system, biggish swap  partition (~8Gb) and  whatever is left to /home.

I expect that if you keep your /home folder the majority of the settings  it includes will ship forward to 10.10 though something will likely  bite amongst it.

Maybe just grabbing the ~/.gnome2/keyrings folder will do it for you, although maybe I've missed something in haste - open your home folder in nautilus and press [CTRL]+[H] to reveal hidden files, look for .gnome2

---

### Post by deadalnix on 2011-02-21
I do confirm that moving ~/.gnome2/keyring from old home to the new one works.

Thanks a lot !

---

### Post by robsoles on 2011-02-21
> **deadalnix said:**
> I do confirm that moving ~/.gnome2/keyring from old home to the new one works.

Thanks a lot !

Very welcome and thank-you very much, confirmation is nice for me but, more importantly, very helpful to future viewers of the thread :)

---

