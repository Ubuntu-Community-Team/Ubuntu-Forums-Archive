---
title: "CDROM Access"
date: 2010-04-05
forum: General Help
---

### Post by JJJCR on 2010-04-05
hi guys, trying my hands to get wet on ubuntu..my first post..
i just installed  ubuntu on my laptop.. i don't have GUI installed.

I type ls -l on root directory, i can see  media/cdrom but if i go to the directory on media/cdrom then type ls -l i can't see the contents of my disc.

so any steps i missed out? please help.. a noob in linux world.. Thanks in advance.

---

### Post by lisati on 2010-04-05
You might have to mount the CD, e.g.
```
sudo mount /media/cdrom
```
It will ask for your password, which won't show: just type normally.
You should then be able to look in /media/cdrom0 to find your files.

---

### Post by JJJCR on 2010-04-06
> **lisati said:**
> You might have to mount the CD, e.g.
```
sudo mount /media/cdrom
```It will ask for your password, which won't show: just type normally.
You should then be able to look in /media/cdrom0 to find your files.

thanks i was able to view the ubuntu disc installer but if i insert another disc like an audio disc i'm unable to view..it shows device i/o error,sector 64 

what could be the problem?

---

### Post by 3rdalbum on 2010-04-06
> **JJJCR said:**
> thanks i was able to view the ubuntu disc installer but if i insert another disc like an audio disc i'm unable to view..it shows device i/o error,sector 64 

what could be the problem?

Audio CDs are not data discs and therefore aren't mountable. If you use a CD player program it should just be able to read the disc.

---

### Post by JJJCR on 2010-04-06
thanks for the input, therefore i can only read data disc..is that what you mean? video disc would not be readable also? sorry still trying to learn this nice OS.. :)

---

### Post by 3rdalbum on 2010-04-07
You can use audio CDs and VCDs, but you can't mount  them.

You're a new user without a GUI? You're kinda jumping into the deep end?

---

### Post by JJJCR on 2010-04-07
okay, so once i mount i don't have to do it again, right? 

i just place the disc on the cd drive and i should be able to read the data, is that how it works?

regarding the gui, i tried to install but it has an error.. i post on another forum categories.. please help..


Thanks.

---

