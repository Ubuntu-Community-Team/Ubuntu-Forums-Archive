---
title: "Jaunty segfault a lot..."
date: 2009-06-28
forum: General Help
---

### Post by EvilBro on 2009-06-28
Recently I've been experiencing a lot of suddenly terminating programs. At first I though this might point to some faulty memory, but a memory scan didn't point to any problems.

I started looking at the logs and in 'messages' I've found numerous logs like:

[   92.603630] gnome-panel[3324]: segfault at fdffefff ip b7767902 sp bffde810 error 4 in libgobject-2.0.so.0.2000.1[b7742000+3c000]

[   93.044310] nm-applet[3338]: segfault at 8088540 ip b7554ff8 sp bfc9feec error 7 in libz.so.1.2.3.3[b7546000+14000]

[ 2983.787220] nautilus[3320]: segfault at bfe3fffb ip b7a19902 sp bff9a820 error 4 in libgobject-2.0.so.0.2000.1[b79f4000+3c000]

[ 2990.538369] nautilus[5434]: segfault at bc8a8732 ip bc8a8732 sp bfe875f0 error 4

[ 1596.672909] rhythmbox[4651]: segfault at 499d92f0 ip b70e3902 sp af158870 error 4 in libgobject-2.0.so.0.2000.1[b70be000+3c000]

What is going on here? What can I do to figure out what the problem is? and how might I fix it?

---

### Post by EvilBro on 2009-06-29
I have an additional question: I use epiphany as a webbrowser and it crashes as well. It doesn't leave any trace in the logs though. I did start it in a terminal and it also said 'segfault'. Is there a way to start epiphany as that it produces more information on the crash?

---

### Post by Psyphre on 2009-07-10
me 2!

Recently everything is segfaulting, GIMP, image viewer, evolution, nautilus etc etc etc. As a results programs just randomly close. Its insanely frustrating.

Did a memtest and it came back fine.

edit: im seeing libgobject-2.0.so appear in all my crash messages too

---

### Post by vonkemp on 2009-07-19
Same here, libgobject-2.0.so.0.2000.1 segfaulting nautilus mainly, but also evolution etc. Only seems to happen on my 64 bit install, 32 bit stuff is fine...

---

### Post by Psyphre on 2009-07-19
> **vonkemp said:**
> Same here, libgobject-2.0.so.0.2000.1 segfaulting nautilus mainly, but also evolution etc. Only seems to happen on my 64 bit install, 32 bit stuff is fine...

Do you have global menu installed? Thats what caused it for me. When i disable it, I dont get any errors.

---

### Post by vonkemp on 2009-07-20
Yes, I do use global menu as it happens - I've disabled it and no segfaults so far today... Thanks for the tip!

It's a shame though because I like(d) global menu. :( I did a little nosing round with the googler and looks as if this issue affects 64 bit installs on multi-processor systems (duos and quads etc.) Something to do with threading or somesuch.

---

### Post by EvilBro on 2009-07-30
I have recently vacuumed the inside of my computer and the crashes seem to have gone away. Maybe some thermal issue or something in my case?

---

### Post by Psyphre on 2009-07-30
> **vonkemp said:**
> Yes, I do use global menu as it happens - I've disabled it and no segfaults so far today... Thanks for the tip!

It's a shame though because I like(d) global menu. :( I did a little nosing round with the googler and looks as if this issue affects 64 bit installs on multi-processor systems (duos and quads etc.) Something to do with threading or somesuch.

Yeh i like it too. Infact i like it so much im keeping it on even if i have to put up with the occasional crash. Could you do me a favour and report it? Ive reported it but have got no response from devs about it.

Heres the thread:
[http://ubuntuforums.org/showthread.php?p=7680872#post7680872](http://ubuntuforums.org/showthread.php?p=7680872#post7680872)

Heres the bug lists:
[http://code.google.com/p/gnome2-globalmenu/issues/list](http://code.google.com/p/gnome2-globalmenu/issues/list)

---

### Post by Psyphre on 2009-07-30
> **EvilBro said:**
> I have recently vacuumed the inside of my computer and the crashes seem to have gone away. Maybe some thermal issue or something in my case?

Oh how strange. I wouldnt have thought thermals would cause it though. Wierd coincidence maybe?

---

### Post by EvilBro on 2009-07-31
> **Psyphre said:**
> Oh how strange. I wouldnt have thought thermals would cause it though. Wierd coincidence maybe?
Maybe... if I am lucky I'll never find out.

---

### Post by dsmorgan6922 on 2009-08-15
How do you disable/remove global menus? I'm getting tons of segfaults too and I hope this is the answer.

---

### Post by Psyphre on 2009-08-15
> **dsmorgan6922 said:**
> How do you disable/remove global menus? I'm getting tons of segfaults too and I hope this is the answer.

Right click it, go to preferences, untick the first option. Let us know if it solves it.

---

### Post by bchurchill on 2009-08-15
> **Psyphre said:**
> Oh how strange. I wouldnt have thought thermals would cause it though. Wierd coincidence maybe?

I've had issues with crashes from overheating before, but I'm pretty sure that it's mostly software issue with multithreading on 64bits that other people are having from the discussion above.

---

### Post by dougie173 on 2009-09-17
I've been having the same problem, just this morning moblock, firefox, totem have all segfaulted. However I don't have global menus installed so there must be something else causing this

---

### Post by Psyphre on 2009-09-17
> **dougie173 said:**
> I've been having the same problem, just this morning moblock, firefox, totem have all segfaulted. However I don't have global menus installed so there must be something else causing this

If its not global menu, have u tried a memtest? Maybe its  your ram.

---

### Post by dougie173 on 2009-09-17
Yes run memtest twice and got no failures. So it must be something else I think

---

### Post by Psyphre on 2009-09-17
odd. Afraid I dont have any ideas for you :(

---

