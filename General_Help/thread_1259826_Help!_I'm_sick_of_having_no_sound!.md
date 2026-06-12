---
title: "Help! I'm sick of having no sound!"
date: 2009-09-06
forum: General Help
---

### Post by Jonathan.N on 2009-09-06
Hello everyone. Well, yeah essentially I never had any sound on linux ever since I installed ubuntu. I have a dual boot Windows XP/Ubuntu 9.04, and sound worked on XP before the entire OS went down (but that's another issue, and I'm 99.9% sure it is'nt related).

Now, I have read multiple threads and posts, articles on different websites and faq's and what not, and nothing seems to work. Now I'm not even sure if there is any kind of sound configuration at all on this machine! If there is one, I definately messed it up more than it was. So before I do any further damage, could someone help me, even if its probably a bug thats already solved and completely documented? It would be greatly appreciated...

I must say I probably made some kind a dumb mistake, because I'm a very new linux user. I am however usually quite competant with computers ( I guess), probably exactly why I switched from Windows. Anyways, I'm just saying I don't just want someone to fix this for me like a slave, I want to learn and understand how this OS works. Thank you in advance for your help :D


[RIGHT]Sincerly, Jonathan N.
[/RIGHT]

---

### Post by Hosmion on 2009-09-06
Let me make a YouTube video real quick, to show you how..  Hopefully it will work :D

Watch the video [HERE]("http://www.youtube.com/watch?v=IOCW8F-7Ztc")

And make sure the volume is actually up :D

---

### Post by bridgetothesun on 2009-09-06
I noticed the sound on my install of Ubuntu 9.04 was really really low. In fact its volume scale was nonlinear, it would be very low and then once I bumped it up high enough it shot up to too loud. 

I wonder if this is related...

---

### Post by Vaphell on 2009-09-06
any details? audio chipset?

---

### Post by Jonathan.N on 2009-09-06
> **Hosmion said:**
> Let me make a YouTube video real quick, to show you how..  Hopefully it will work :D

Watch the video [HERE]("http://www.youtube.com/watch?v=IOCW8F-7Ztc")

And make sure the volume is actually up :D

I don't have any options for device anymore. Its like I said, I pretty sure I messed this up even further... And even remember what I did, cuz I tried so many things that barely even made sense to me since I'm all new to linux..... Gosh, this is getting out of hand.

Thanks for the quick replies though! Really appreciated!

---

### Post by Jonathan.N on 2009-09-06
> **Vaphell said:**
> any details? audio chipset?

How do you get to know that again? I forgot to write it down.

---

### Post by bridgetothesun on 2009-09-06
and not to hijack, but can anyone help me with my nonlinear volume scale?

---

### Post by sailthesea on 2009-09-06
This guide ,if you haven't already looked at it, should help you purge and reinstall media support 
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Hosmion on 2009-09-06
> **Jonathan.N said:**
> How do you get to know that again? I forgot to write it down.
If you had deleted, I would suggest deletion of UBuntU and re-installation..

---

### Post by Vaphell on 2009-09-06
to get the list of hardware use ```
hwinfo --short
``` and detailed info about audio ```
hwinfo --sound
```

---

### Post by pramtung on 2009-09-06
try..
```

lspci | grep Audio

```

If it return some value, that's mean you just need to install ALSA Driver, ALSA etc..

If it doesn't return anything, .... :confused:

---

### Post by ndefontenay on 2009-09-06
I have the non linear sound problem as well on a laptop.
I took it that linux was just crappy handling sound volume :x

Let's open a new thread for that one. I would love to have it fixed as well.

edit: Thread open here for that one
[http://ubuntuforums.org/showthread.php?p=7909576#post7909576](http://ubuntuforums.org/showthread.php?p=7909576#post7909576)

---

### Post by utnubuuser on 2009-09-07
I've used this [http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578") guide to pulse and it's worked.

---

