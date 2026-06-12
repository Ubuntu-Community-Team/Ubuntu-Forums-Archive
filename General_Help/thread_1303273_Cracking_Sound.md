---
title: "Cracking Sound?"
date: 2009-10-28
forum: General Help
---

### Post by ambdeep on 2009-10-28
I had an unclean shutdown on linux......after that my sound stopped working and i get a soft crackling sound instead......please help....thanks in advance!!!

---

### Post by rockstarrem on 2009-10-28
Just wondering, what sound card do you have?

---

### Post by JBAlaska on 2009-10-28
Better just FSCK it then...Sorry could not resist. What sound hardware are you using, software ALSA or OSS?

---

### Post by theozzlives on 2009-10-28
I would start with the live CD, run
```
sudo fsck /dev/sda1
```
there may be Filesystem errors. Are you using ext3 or 4?

---

### Post by JBAlaska on 2009-10-28
I did not mention this because he would be automatically FSCK'd on reboot, Of course it would always be a good idea to FSCK yourself manually as you discribed...

---

### Post by ambdeep on 2009-10-28
im using ext4......how exactly do i FSCK without the live cd......does this format the system?......also was using ALSA then changed to OSS after reading a post on another thread......the sound after booting now works....but now the sound comes during boot.....thanks for all the replys.....could you also tell me how to check for what hardware i have......i dont know how to do it on linux........thanks again.....

---

### Post by JBAlaska on 2009-10-28
Anytime you have a bad "unclean" shutdown FSCK will run on reboot (It will NOT format your drive), also it runs after a certain number of boot cycles (Don't remember the number 20? I think). 
It's best to run a file system check from a LiveCD without mounting the hard drive. Most LiveCDs won't mount the hard drive anyway unless you tell them to, but they usually do use the swap area.
You should never run a file system check on a mounted partition.

There are many ways to view different hardware item's For this instance I believe ```
lspci
``` would be your best bet.

Glad your sound is working now!

---

