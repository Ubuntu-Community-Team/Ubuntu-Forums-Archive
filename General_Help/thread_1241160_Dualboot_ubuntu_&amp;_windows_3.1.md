---
title: "Dualboot ubuntu &amp; windows 3.1"
date: 2009-08-15
forum: General Help
---

### Post by dutchy131 on 2009-08-15
Okay guys, i have installed ubuntu like a couple of months ago but i would like also to dualboot ubuntu & windows 3.1 .

Now i have this problem ubuntu is first installed and i think grub will get overwriten by windows 3.1 ,how can i solve this problem?
also if this is in the wrong section please move it to another section. 
:P:confused:
Thanks in advance.

---

### Post by GoldenSun on 2009-08-15
i dont understand your problem.
You have ubuntu and you want to install father time (win 3.1) but are worried that it will erase the files you have?

that's a guess on the problem.

---

### Post by dutchy131 on 2009-08-15
> **GoldenSun said:**
> i dont understand your problem.
You have ubuntu and you want to install father time (win 3.1) but are worried that it will erase the files you have?

that's a guess on the problem.
No i don't want to install windows over ubuntu.
But i readed that if you install ubuntu first and then windows it will overwrite grub.
-----
Edited it so it's clear
I'm dutch so i kinda still learning english.

---

### Post by GoldenSun on 2009-08-15
oh that makes sense now lol

install windows and let it wipe out grub.
boot from linux live cd.

then type these in terminal
```

sudo grub
 root (hd0,0)
 setup (hd0)
 exit

```

---

### Post by running_rabbit07 on 2009-08-15
I would definitely recommend backing up your Ubuntu files. I wish I could get my hands on some of those old install disks.

---

### Post by dutchy131 on 2009-08-15
> **GoldenSun said:**
> oh that makes sense now lol

install windows and let it wipe out grub.
boot from linux live cd.

then type these in terminal
```

sudo grub
 root (hd0,0)
 setup (hd0)
 exit

```
Thanks will try it. :guitar::P

---

### Post by dutchy131 on 2009-08-15
> **GoldenSun said:**
> oh that makes sense now lol

install windows and let it wipe out grub.
boot from linux live cd.

then type these in terminal
```

sudo grub
 root (hd0,0)
 setup (hd0)
 exit

```
Hmm 1 last thing i can install windows on another partition and then use this right?

---

### Post by dutchy131 on 2009-08-15
> **running_rabbit07 said:**
> I would definitely recommend backing up your Ubuntu files. I wish I could get my hands on some of those old install disks.
I don't have those i just kinda download windows 3.1  x) it's cool on a kinda old laptop,compaq armada e500

---

### Post by P4man on 2009-08-15
3.1 lol!
Some time ago, I was tempted to install OS/2 warp on virtualbox for a laugh when i came across a few very old cds. But then I found out (again) that warp doesn't install from cd, the cd  only has dos tools to make like 30 or so  1.44Mb *floppies* to install from and I gave up lol. Unless someone knows a clever way to make warp install from floppy images without a floppy drive somehow?

---

### Post by dutchy131 on 2009-08-15
> **P4man said:**
> 3.1 lol!
Some time ago, I was tempted to install OS/2 warp on virtualbox for a laugh when i came across a few very old cds. But then I found out (again) that warp doesn't install from cd, the cd  only has dos tools to make like 30 or so  1.44Mb *floppies* to install from and I gave up lol. Unless someone knows a clever way to make warp install from floppy images without a floppy drive somehow?
I got this realy old laptop from my dads work it was laying in the container 
:lolflag:
I also do it for the fun .

---

### Post by dutchy131 on 2009-08-15
> **GoldenSun said:**
> oh that makes sense now lol

install windows and let it wipe out grub.
boot from linux live cd.

then type these in terminal
```

sudo grub
 root (hd0,0)
 setup (hd0)
 exit

```
did it grub gives error 17 when booting i now am booting the live cd and will try it as soon as live cd is booted !

---

