---
title: "Folder not showing content."
date: 2009-12-09
forum: General Help
---

### Post by ExSuSEusr on 2009-12-09
Running 9.10.  I have some old video files from classes I took some time ago.  Put them in my "Videos" folder, but they wont display.  Ok let me explain.  When I reboot and go to the Video folder - I can see them, click on them, activate them, etc.  Once I watch one and shut it down and close the Videos folder - when I go to reopen the Video folder nothing happens.  The folder opens but then it sits there with the "hour glass" spinning away but wont display the files.

What is going on?

---

### Post by StuartN on 2009-12-09
> **ExSuSEusr said:**
> The folder opens but then it sits there with the "hour glass" spinning away but wont display the files

Perhaps you do not have the right codecs, so the preview image can not be built. You could disable previews in Nautilus preferences to see if this lets you get on with life, and if it does then try viewing the videos in your preferred application.

Vlc seems to do a grand job of installing all the usual codecs.

---

### Post by SuperSonic4 on 2009-12-09
ubuntu-restricted-extras is better but it will install crap like java and flash

Does ```
ls -Ar ~/Videos
``` recognise them

---

### Post by t0p on 2009-12-09
Hmm.  I don't think it's a codec issue.  The OP says he can see the files in the directory after a reboot; it's after he watches a video that the directory appears to be empty.

But SuperSonic4 is on the right lines.  OP, open a terminal and type in the command:

```
ls -a ~/Videos
```and post the output here.

---

### Post by ExSuSEusr on 2009-12-09
He all, 

Here's what I get with the above code.

```
ls -Ar ~/Videos
FlashZjFUbm  Flashx3AWA0  FlashPAWUcf  FlashksJUlh  FlashE3Qme1  Flash5BvXYD
FlashZ5GCSQ  FlashVuARsW  FlashoIHK0d  FlashJAYNZK  FlashbNE8FC  Flash2U0Udr
FlashxZAwRO  FlashtL23j2  FlashNZaOqe  FlashHvDvpl  Flashb80zwR
FlashXOszDc  FlashqJV72n  FlashlMnjwj  FlashHmiLmk  Flash7XwpAy

```

---

### Post by llamabr on 2009-12-09
Well, there they are then.  In the mean time, you can use the terminal to move to that directory, and play them from the command line, with mplayer:

```
mplayer Flashdfheug
```

That'll get you working, until someone can sort out your gnome settings.

---

