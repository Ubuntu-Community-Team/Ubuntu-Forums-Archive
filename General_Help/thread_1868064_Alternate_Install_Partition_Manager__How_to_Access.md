---
title: "Alternate Install Partition Manager:  How to Access?"
date: 2011-10-23
forum: General Help
---

### Post by _Ouroboros_ on 2011-10-23
[FONT=Arial]The Ubuntu Alternate CD installer has a very good partition manager.

Is there any way to access this Partition Manager outside of the installer?  And if so, what is the package called that contains it?  If not, how does one run the installer without booting from the CD[/FONT]?

---

### Post by Gadgetech on 2011-10-23
I'm not sure which partition manager is used in the alternate install CD, but GParted is an easy graphical one to use. You can install it with
```
sudo apt-get install gparted
```

---

### Post by _Ouroboros_ on 2011-10-23
Thanks for the reply, but I already know about gparted though.  The Partition Manager featured in the Alternate CD Installation easily allows me to change how many blocks are reserved on each partition, change the usage from news, standard, largefile, etc.  It has several features which to my knowledge, gparted lacks.

---

### Post by Gadgetech on 2011-10-23
cfdisk is another option, although I don't have experience using it. It should already be available on your system. Don't know if it has all of the options you mentioned though.

---

### Post by Gadgetech on 2011-10-23
OK, I'm guessing it's partman that is used by the alternate CD. It can be found in the ubiquity package.
```
sudo apt-get install ubiquity

```
Then launch with
```
sudo partman
```

---

### Post by _Ouroboros_ on 2011-10-23
Thanks.  It is indeed "partman"!

---

