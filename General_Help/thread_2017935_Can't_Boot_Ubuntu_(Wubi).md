---
title: "Can't Boot Ubuntu (Wubi)"
date: 2012-07-05
forum: General Help
---

### Post by theopfor on 2012-07-05
I read [this article]("https://help.ubuntu.com/community/AA1/Using") for my Acer Aspire One 532h. I read a lot and I tweaked it, so I hope I didn't break more than what I think. I changed the rc file in /etc/init.d so my computer would boot faster, and I saw the warning about karmic, but I use 12.04, so I ignored it. So now my computer boots to the part where I select Ubuntu or Windows (I dual boot), and to recovery or regular, next I see "ubuntu" with the loading dots, and the screen goes black.

I was able to get some software for Windows that would allow me to view my Ubuntu files, so I got the gedit backup and tried going into recovery to fix it (I changed CONCURRENCY from shell back to makefile).

```
cp /host/Users/mattman/Desktop/rc /etc/init.d/rc
```I tried using sudo before cp too, but neither worked. I've been messing with it for a couple hours now, and nothing I have done has helped. I am willing to try almost anything now.

Does anyone know how to fix this? I am dual booting, and I have tried multiple programs.

---

### Post by Bucky Ball on 2012-07-05
I can't help you with your pickle but will add this (all good in hindsight): *Always* save a backup copy of any file you intend to tweak ***before*** you start tweaking! For important files like the one you're working it is a must; make it a healthy habit. Good luck. ;)

(Just thinking the 'original' file is on the install CD somewhere I'd imagine. Maybe you could drag it from there.)

---

### Post by theopfor on 2012-07-05
I do have backup copies of the files, but that is nothing I have actually considered before, and I will remember it.

---

### Post by theopfor on 2012-07-06
Bump

---

### Post by wilee-nilee on 2012-07-06
Use a Live Ubuntu cd for your tweaking never do it from windows, same for tweaking the other direction basically.

Windows may not render the tweaks correctly although here you are probably okay.

I would rely more on help on the forums for doing this in general, many here have SSD, and following one for a end of life that has a warning is not really thinking through what you your doing to be honest. ;)

---

### Post by Ceannfaolaidh on 2012-07-06
Extending on the usefulness of the LiveCD, you can use it to access the files on the broken system if you happen to need them. You can also use GParted to check your partitions, though I doubt that's the problem.

---

### Post by theopfor on 2012-07-06
My computer doesn't have a CD drive. I have tried a USB once and I couldn't see my Ubuntu files.

---

### Post by wilee-nilee on 2012-07-06
> **theopfor said:**
> My computer doesn't have a CD drive. I have tried a USB once and I couldn't see my Ubuntu files.

Is this a wubi install? That is a install from windows, if so then trying to make it boot faster by tweaking is probably not suggested, the boot is slightly different all of grub is not there as a partitioned dual boot would have.

---

### Post by theopfor on 2012-07-06
Yeah, it's wubi that installed it.

---

### Post by wilee-nilee on 2012-07-06
> **theopfor said:**
> Yeah, it's wubi that installed it.

I would hit the report abuse to get the mods a message to add wubi to the thread title. Its not abuse and no big deal to get this added, it will raise the likely hood of you getting help a great deal.

Getting a hold of them this way is the fastest path.

---

### Post by Bucky Ball on 2012-07-06
> **wilee-nilee said:**
> I would hit the report abuse to get the mods a message to add wubi to the thread title. Its not abuse and no big deal to get this added, it will raise the likely hood of you getting help a great deal.

Getting a hold of them this way is the fastest path.

+1. A wubi install is a different kettle of fish ... Good luck. ;)

---

### Post by theopfor on 2012-07-06
Thanks, just did. I had a problem last month where people in another forum weren't really helping, but I understand now that it was because I didn't state that I used wubi.

---

### Post by theopfor on 2012-07-07
Bump.

---

### Post by theopfor on 2012-07-07
Anyone?

---

