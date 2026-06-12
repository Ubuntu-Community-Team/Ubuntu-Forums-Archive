---
title: "access priveledges for mounted hdd's"
date: 2006-05-04
forum: General Help
---

### Post by Melciah on 2006-05-04
this question really suggests how much of a newb i still am. this is probably easily fixed.

how do i change the access priveledges of my mounted drives at startup. im guessing i need to modify my fstab.

just so its clear, i want to be able to save files onto one of my mounted fat32 drives without the bother of first copying it to my ext3 partition and then using a terminal to copy it over.

really, i just want to be able to use p2p progs and let them save to the mounted drive without these extra steps. I get a write permission problem when i try it.

one more question while im at it. why cant i copy files larger than 4gb between my ext3 partition and my fat32?

---

### Post by ruzle0 on 2006-05-04
the option umask=000 if you want any user to be able to write to the partition eg.
edit: in your /etc/fstab
       sudo gedit /etc/fstab

put something like
```
/dev/hda5       /media/win_share vfat   umask=000       0       0
```

if you want to do something more specific, eg specific users and permisions say so and i'll help you out

---

### Post by Melciah on 2006-05-05
thanks man. using this method is a tradeoff, because i want to be able to save to the hdd, but i dont want users to delete files from it without root permission.

---

