---
title: "Can't open Home folder"
date: 2010-03-20
forum: General Help
---

### Post by Liso22 on 2010-03-20
Nothing is shown on the desktop and trying to access home or any folder inside gives me an error which says:

Could not open location 'file:///home/lisandro'
No application is registered as handling this file

---

### Post by rnerwein on 2010-03-20
hi
my first question: is your home folder on a seperate partition ?
if yes than it seems your partiton isn't mouted due to an error on the  filesystem.
type ( in a terminal) : mount - to figure this out. if it is not mounted than run fsck on  your /home partition.
--> sudo fsck /dev/sdaX  ( where X is the partition of your /home )
then type: mount -a
logout and login again.
hope this help you
ciao

---

### Post by n0dix on 2010-03-20
> **Liso22 said:**
> Nothing is shown on the desktop and trying to access home or any folder inside gives me an error which says:

Could not open location 'file:///home/lisandro'
No application is registered as handling this file

Maybe a problem with permissions. 
Open a console, Alt+F2, then write xterm and Enter.
Do:
```
$ ls -la /home/ 
```

---

### Post by Liso22 on 2010-03-20
thanks I ended up reinstalling Ubuntu, I do have home on a separate partition so it wasn't a big deal, thanks anyway

---

### Post by sideaway on 2010-04-16
Hey, I'm having the same issue, I was playing around with Media handling under the media tab in Nautilus' preferences... Any ideas? None of the two suggested worked, my home folder is mounted and I have ownership.

---

### Post by sideaway on 2010-04-16
Bump :)

---

### Post by sideaway on 2010-04-17
Can anyone please help?

---

