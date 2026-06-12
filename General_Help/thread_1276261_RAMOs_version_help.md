---
title: "RAM/Os version help"
date: 2009-09-26
forum: General Help
---

### Post by es305 on 2009-09-26
Not sure how to check if my ubuntu is 64 bit, I checked my total ram and it reads 3.5g out of a possible 6, was wondering how I can verify if it's 32 or 64, and if it's 32 how would I be able to upgrade it to 64 bit (without losing any files if possible) thus allowing me to use all 6 gigs that I currently have installed.


(this is what comes up when you type uname -a in the terminal)

Linux evan-desktop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

---

### Post by renkinjutsu on 2009-09-26
it says i686, so no, it's not 64 bit =[

---

### Post by JC Cheloven on 2009-09-26
Furthermore, if you have 6Gb of physical ram, and only 3.?? are taken into account, this is a very strong clue. If you were on 64 bits, the 6Gb would be recognised ;-)

---

### Post by renkinjutsu on 2009-09-26
you can check if your CPU is 64bit capable

```
lshw -c cpu
```
and look around under the list "capabilities"

---

### Post by es305 on 2009-09-26
Ah, alright thanks. Now for my second question would I be able to upgrade to a 64 bit client without losing anything off of my hard drive?

(I checked using that command and it is in fact capable of running a 64 bit client)

---

### Post by lisati on 2009-09-26
> **es305 said:**
> Ah, alright thanks. Now for my second question would I be able to upgrade to a 64 bit client without losing anything off of my hard drive?

By "client" I assume you mean Ubuntu. A fresh install of the relevant OS is the usual way to go. Don't forget to make backups of important data first, particularly if you don't have a separate partition for your /home directory.

---

### Post by es305 on 2009-09-26
> **lisati said:**
> By "client" I assume you mean Ubuntu. A fresh install of the relevant OS is the usual way to go. Don't forget to make backups of important data first, particularly if you don't have a separate partition for your /home directory.

Yeah heh forgive me for being vague I meant a 64 bit version of Ubuntu. So if I backup all my files I would be able to go 64, and if you don't mind me asking how would I in fact back up my files prior to them reformat? or would I have to do that while I was reformating? (forgive me for all the questions, would just hate to lose all of my data. ](*,)

---

### Post by lisati on 2009-09-26
The simplest way of doing a backup of your important data files (which sounds more complicated than it really is) is to copy the contents of your /home directory to a CD, DVD or another disk partition or disk drive. You'd need to do this before you format your drive.

---

### Post by es305 on 2009-09-26
> **lisati said:**
> The simplest way of doing a backup of your important data files (which sounds more complicated than it really is) is to copy the contents of your /home directory to a CD, DVD or another disk partition or disk drive. You'd need to do this before you format your drive.

Heh, that's it? I figured it would have involved a bit more than that. In any case, thank you very much :biggrin:

---

