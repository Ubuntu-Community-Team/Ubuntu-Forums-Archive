---
title: "Rythembox and Movieplayer Problems"
date: 2009-09-03
forum: General Help
---

### Post by Twistedsnail on 2009-09-03
Hey everyone!

I have 2 very similar problems:

1) When I try to start up rythembox it says 'opening rythembox' then that disappears and nothing opens!


2) When I try to start up movieplayer it says 'opening movieplayer' then that disappears and nothing opens!

Why don't they work its really annoying!:confused:

---

### Post by Twistedsnail on 2009-09-03
Bump!

please help

---

### Post by ad_267 on 2009-09-03
Open a terminal from Applications - Accessories - Terminal then enter these commands and post the output here (totem is the movie player):
```
totem
```
```
rhythmbox
```

---

### Post by Twistedsnail on 2009-09-05
```
twistedsnail@twistedsnail-laptop:~$ totem

** (totem:3469): WARNING **: Could not import pygtk
ImportError: No module named pygtk
Segmentation fault
twistedsnail@twistedsnail-laptop:~$ rythmbox
bash: rythmbox: command not found
twistedsnail@twistedsnail-laptop:~$ rhythmbox

(rhythmbox:3475): Rhythmbox-WARNING **: Could not import pygtk
ImportError: No module named pygtk
Segmentation fault
twistedsnail@twistedsnail-laptop:~$ 
```Ok apparently I need pygtk!

Ok i installed it successfully but the output of 'totem' and 'rhythmbox' is this:

```
twistedsnail@twistedsnail-laptop:~$ totem
Segmentation fault
twistedsnail@twistedsnail-laptop:~$ rhythmbox
Segmentation fault
twistedsnail@twistedsnail-laptop:~$ 

```

---

### Post by ad_267 on 2009-09-05
Ooh that's not good (and not very helpful either). Maybe a bit more information would help, it's weird that you didn't have pygtk. What version of Ubuntu is this? And have you tried to compile any software, or install anything from a PPA recently that could have messed this up?

You could install the debugging symbols (totem-dbg and rhythmbox-debug) and run gdb (gnu debugger) to sort out what's going wrong, but my guess is it would be a lot easier just to back up all your stuff and do a clean install.

---

### Post by Twistedsnail on 2009-09-05
ouch!!
 I might just have to do it I guess
could it be that its on my laptop??

ubuntu version 9.04 juanty jackalope

---

### Post by greenco on 2009-09-05
I submitted this on or about 28 July 09 and still don't know why it happens, but maybe it will help someone.
****************************************
I recently upgraded to Ubuntu 9.04 and have run into a small problem with Rhythmbox. The program runs and it plays my music files, but in order for this to happen, I have to open it twice. The first time I click on the "Applications / Sound & Video / Rhythmbox Music Player" to open it, the cursor looks like it is going to open, but nothing happens. If I go back to the "Applications / Sound & Video / Rhythmbox music player" and click on it again it, will open and work fine. The same thing happens when I insert a music CD and nothing happens, but if I eject the CD and insert it again, Rhythmbox will open. Does anyone have any ideas about what may be causing this?
****************************************
It doesn't matter now, because I reverted back to version 8.04

---

### Post by Twistedsnail on 2009-09-06
> **greenco said:**
> I submitted this on or about 28 July 09 and still don't know why it happens, but maybe it will help someone.
****************************************
I recently upgraded to Ubuntu 9.04 and have run into a small problem with Rhythmbox. The program runs and it plays my music files, but in order for this to happen, I have to open it twice. The first time I click on the "Applications / Sound & Video / Rhythmbox Music Player" to open it, the cursor looks like it is going to open, but nothing happens. If I go back to the "Applications / Sound & Video / Rhythmbox music player" and click on it again it, will open and work fine. The same thing happens when I insert a music CD and nothing happens, but if I eject the CD and insert it again, Rhythmbox will open. Does anyone have any ideas about what may be causing this?
****************************************
It doesn't matter now, because I reverted back to version 8.04


I will have to try this!!
it might work...

---

### Post by zipperback on 2009-09-06
> **Twistedsnail said:**
> ouch!!
 I might just have to do it I guess
could it be that its on my laptop??

ubuntu version 9.04 juanty jackalope


I don't think that it being on your laptop would be the problem, unless of course you have some really non-standard hardware or something that is causing problems.

I have an acer aspire 5050-3371 laptop and I've been using rhythmbox for a very long time without any problems.

Could you please post what the specifics are for your laptop?

Also, please let us know if you are running the 32bit or 64bit version of Ubuntu.

One quick suggestion...

```

sudo apt-get update && sudo apt-get upgrade

```

That will update your system with the currently available releases for 9.04

Maybe you're still somehow missing something...

After that try to start them from command line again and post up the responses you get.

- zipperback

---

### Post by Twistedsnail on 2009-09-08
still the same

dammit

---

### Post by P4man on 2009-09-08
its very strange you didn't have pygtk. it should be there by default. I wonder if you deleted some packages mannually, and perhaps removed other stuff you need as well? Try this:

```
sudo apt-get install --reinstal ubuntu-desktop
```

---

### Post by Twistedsnail on 2009-09-09
will that get rid of all my stuff?? do I need to put the cd in!

---

### Post by P4man on 2009-09-09
> **Twistedsnail said:**
> will that get rid of all my stuff?? do I need to put the cd in!

It won't remove anything, it will add and reconfigure whatever default packages you no longer have. Not saying it will help, but it won't hurt.  And no need for the cd. If you have the alternate cd, you can put it in to avoid downloading, but its not needed.

---

### Post by Twistedsnail on 2009-09-10
as long as it won't get rid of stuff i will try it ^^ :D

---

### Post by Twistedsnail on 2009-09-11
Ok fixed!!!

I just installed vlc lol

---

