---
title: "Help with finding appropriate Driver"
date: 2010-06-29
forum: General Help
---

### Post by gingivere0 on 2010-06-29
I am trying to run a game called Savage 2.  However, whenever I start up the game, the screen looks like this:
  [[IMG]http://img692.imageshack.us/img692/4553/screenshot2ha.th.png[/IMG]](http://img692.imageshack.us/i/screenshot2ha.png/)

I'm certain that the problem isn't with the Graphics **Card** because the game runs perfectly under Windows 7 (Dual Boot).  I think the problem might be with the graphics driver. Here is the output of lspci on the VGA line:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
```
Where would I be able to find the best driver for my card and what other system specs could I give you to make solving this problem easier? Thanks for all replies! :)

---

### Post by mikewhatever on 2010-06-30
I think the only place you can find good Intel drivers is the future. Let us hope.;)

---

### Post by gingivere0 on 2010-06-30
I hope you're joking :/

---

### Post by Mark Phelps on 2010-06-30
Well basically, he's not ... joking, that is.

Unlike in Win7, in Ubuntu, the standard Intel video driver is installed as part of setup -- which means, you already HAVE the Intel driver installed and running.

The Intel drivers had major problems with 9.10, and it looks like that legacy of problems may be continuing with 10.04.

My guess is that he was referring to 10.10, which is SUPPOSED to be bringing improvements in the Intel drivers.

---

### Post by mikewhatever on 2010-06-30
I really don't know anything about Intel graphics improvements in 10.10. All I am saying is - Intel graphics are not for gaming, especially not on Linux.

---

### Post by gingivere0 on 2010-06-30
Well that sucks :(  I guess I'll have to wait and see... Thanks for the replies :)

---

### Post by gingivere0 on 2010-06-30
Well that sucks :(  I guess I'll have to wait and see... Thanks for the replies :)

---

