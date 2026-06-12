---
title: "TV Tuner card - SOFTWARE Question"
date: 2006-02-14
forum: General Help
---

### Post by eight_car on 2006-02-14
I just got my TV Tuner card to work.

Now, under the fake OS (as my Linux [Red Hat] Prof called it) The software that came with it allowed me to take a screen snapshot and also record tv programs and even schedule to record tv programs.

I don't see anything like this under tvtime.

Any ideas?

Thanks.

---

### Post by tuxinator on 2006-02-14
I don't have any suggestions but I would like to say that **you are my hero**.  I have a tv tuner card and can't get it to work under linux.  What brand of card do you have and what programs did you use? I got an old ATI TV Wonder card because it was cheap.

Good job getting it working and sorry I couldn't help you out any.

---

### Post by eight_car on 2006-02-14
[QUOTE=tuxinator]I don't have any suggestions but I would like to say that **you are my hero**.  I have a tv tuner card and can't get it to work under linux.  What brand of card do you have and what programs did you use? I got an old ATI TV Wonder card because it was cheap.

Good job getting it working and sorry I couldn't help you out any.[/QUOTE]

There are a couple good threads on getting a TV tuner card to work. I took info from about 2-3 different ones and made it work with that (Thanks everyone!)

Program: tvtime (look under package manager)
Run tvtime first and see if it works, if not then ......
     do a search under tv tuner in the Ubuntu forums and start reading.

My card is a Leadtek WinFast 2000/ WinFast 2000 XP.

Good luck! :)

---

### Post by BoyOfDestiny on 2006-02-14
[QUOTE=eight_car]There are a couple good threads on getting a TV tuner card to work. I took info from about 2-3 different ones and made it work with that (Thanks everyone!)

Program: tvtime (look under package manager)
Run tvtime first and see if it works, if not then ......
     do a search under tv tuner in the Ubuntu forums and start reading.

My card is a Leadtek WinFast 2000/ WinFast 2000 XP.

Good luck! :)[/QUOTE]

I've got the same card (well the xp one). To make screenshots you need to press S. =) As for recording etc... tvtime is made just to be "watched" (I know... I'd love a record feature in it too)

Anyway, check etc/tvtime/tvtime.xml to change some settings (because it has an overlay for screenshots by default, also I had to change the value for the mixer to line1 get sound, since I used the internal audio connection). 

There should be a tvtime.xml in a .tvtime folder in home, I like to change the settings there, since it stays if I reinstall ubuntu etc...

---

### Post by eight_car on 2006-02-14
Thanks for the screenshot tip. That works.

---

### Post by RikoW on 2006-02-15
For recording, I use the kaffeine player, which is a KDE application but runs great under Ubuntu gnome. It also allows you to take screenshot (haven't tried that yet, though). Also, for recording you have the choice of "instant recording" of what you watch and programming timers.

Of course, kaffeine is much more than just a TV application, it's a full featured meadia player. You can install it via synaptic of apt

My TV card is a Cinery T2 DVB-T card. and it works great under Linux.

Cheers,

             Riko

---

