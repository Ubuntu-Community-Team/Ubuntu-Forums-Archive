---
title: "Difragmentation Utility?"
date: 2006-04-08
forum: General Help
---

### Post by junglemike on 2006-04-08
Is there any difrag utility for Kubuntu, or at least any way to see how fragmented disk is? (and i feel that it IS fragmented..)

---

### Post by Brando569 on 2006-04-08
they dont get fragmented. if you really want to you can search freshmeat

---

### Post by dreamsINdigital on 2006-04-08
Linux doesn't need to be defragmented because it handles files more efficiently than Windows.  It shouldn't be fragmented.  Judging by your computer specs, your computer is just slow.

---

### Post by junglemike on 2006-04-08
Yes, I agree my computer is slow, but how do you eplain this?
```
junglemike@PII-300:~$ sudo hdparm -t /dev/hda
Password:

/dev/hda:
 Timing buffered disk reads:   18 MB in  3.13 seconds =   5.75 MB/sec
junglemike@PII-300:~$ sudo hdparm -t /dev/hda

/dev/hda:
 Timing buffered disk reads:   32 MB in  3.22 seconds =   9.92 MB/sec
junglemike@PII-300:~$ sudo hdparm -t /dev/hda

/dev/hda:
 Timing buffered disk reads:   46 MB in  3.05 seconds =  15.06 MB/sec
junglemike@PII-300:~$ sudo hdparm -t /dev/hda

/dev/hda:
 Timing buffered disk reads:   44 MB in  3.08 seconds =  14.30 MB/sec
junglemike@PII-300:~$ sudo hdparm -t /dev/hda

/dev/hda:
 Timing buffered disk reads:   42 MB in  3.15 seconds =  13.34 MB/sec

```

Same command run 4 times in a row (w/o doing any changes). Why speed is slow at start and then  improves?
Can anybody run this command on any modern computer and post the result, I just want to see if this laptop disk is really slow, or not that bad?

---

### Post by Sef on 2006-04-08
> Computer specs: P-II-300mhz cpu @66 mhz 128mb ram 

I would expect Kubuntu (and Gnome) to run slow on your machine.  An alternative window manager would run faster on your machine.

Download icewm, fluxbox (the lightest), or xubuntu.

sudo apt-get update

sudo apt-get install (window manager name)

---

### Post by junglemike on 2006-04-08
> I would expect Kubuntu (and Gnome) to run slow on your machine. An alternative window manager would run faster on your machine.

Download icewm, fluxbox (the lightest), or xubuntu.

Yes, I already tried Xfce4 - but it is just too uncommon for me. I've not get used to it. KDE looks really good, and allows more customization. I already swiched off all eye candy. I'm now playing with services startup to speed up little bit. 

Question:
What would be the command in Ubuntu to choose what window manager is used as default? Let's say i install IceWM, but how do i switch to kde, if i don't like icewm?

---

### Post by bailout on 2006-04-09
when you login you will be able to choose a kde or icewm session. You can also set which is default.

---

