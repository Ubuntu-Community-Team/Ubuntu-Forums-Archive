---
title: "Anyway to reset Video Card Drivers to default?"
date: 2010-06-24
forum: General Help
---

### Post by Zolbad on 2010-06-24
So I was messing around with Ubuntu trying to make somethings work. Then i rebooted ,and I wasn't able to turn on Visual Effects. So I'm guessing that I must have replaced my video card driver with a non-compatible one or just removed it without knowing. 
 
  So I was wondering "**How Can I Switch Back To The Video Card Driver Ubuntu Came With?**" * Without reinstalling* *Ubuntu?* Since I was able to at least switch on Visual Effects with it.

[CENTER]*And could you also take a look at:[ http://ubuntuforums.org/showthread.php?p=9505616]("http://ubuntuforums.org/showthread.php?p=9505616")*
[/CENTER]


[B]  Please someone help,
Zolbad
[/B]

---

### Post by Serpher on 2010-06-24
Im not completely sure on all of this, but I'm pretty sure drivers are complied into your kernel. I think the way you fix this is somehow replace your current kernel. Im pretty sure there's an image file or something somewhere in /boot. If you can't find a file just download the source for it probably somewhere on Ubuntus' website. Ubuntu is required to have the source code for every part of their OS. If you want help compiling it just say so.

---

### Post by VH-BIL on 2010-06-24
what things where you messing with? can you go system > administration > hardware drivers and activate one?

---

### Post by Zolbad on 2010-06-24
_VH-BIL: _I'm not a very experienced Ubuntu user, and all that program seems to do is search for available drivers...and the only one it gives me is for some modem stuff, which i do not need.

_Serpher_: As you might have noticed, I'm not too experienced in using Ubuntu :(. So could you give me more detailed instructions on how to try to get the default driver without reinstalling?

EDIT: Just searched /boot and there seems to be two Image files: **initrd.img-2.6.32-21-generic **And **initrd.img-2.6.32-22-generic**

---

### Post by clhsharky on 2010-06-24
Zolbad

In terminal

```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
sudo dpkg-reconfigure xserver-xorg
sudo restart gdm
```

Sharky

---

### Post by Zolbad on 2010-06-24
_Sharky:_ Thanks a tonn :D It's working nicely again. Oh and could you take a look at my other bigger problem? [http://ubuntuforums.org/showthread.php?p=9505616](http://ubuntuforums.org/showthread.php?p=9505616)

Well thanks again, took a few hours to find an answer to that question..

---

### Post by VH-BIL on 2010-06-24
> **Zolbad said:**
> _Sharky:_ Thanks a tonn :D It's working nicely again. Oh and could you take a look at my other bigger problem? [http://ubuntuforums.org/showthread.php?p=9505616](http://ubuntuforums.org/showthread.php?p=9505616)

Well thanks again, took a few hours to find an answer to that question..

Glad it is working for you :)

---

### Post by Zolbad on 2010-06-24
Thanks.

---

### Post by asdir on 2011-03-04
> **clhsharky said:**
> Zolbad

In terminal

```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
sudo dpkg-reconfigure xserver-xorg
sudo restart gdm
```

Sharky

Is this still valid for 10.10? 

I think there were major changes with respect to Xorg and I'm afraid to break my productive machine by trying the solution.

edit: sry for the necromancy, btw

edit2: Tried it, didn't break anything, but didn't fix the issue for me either... :-S

---

