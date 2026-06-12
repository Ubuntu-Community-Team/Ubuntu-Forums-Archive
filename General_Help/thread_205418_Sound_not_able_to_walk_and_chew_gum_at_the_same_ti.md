---
title: "Sound: not able to walk and chew gum at the same time"
date: 2006-06-28
forum: General Help
---

### Post by Marcos.Rufino on 2006-06-28
When I'm with amaroK (with xine engine) opened, I couldn't hear the sound from some other sources, like sound streaming from, for example, Zdnet website. 

This problem occurs even when I'm hearing nothing from amaroK!!
So, I've got to close amaroK, open the terminal, "killall esd", and then voilá. When I come back to amaroK, it tries to play every song in the playlist, jumping from one track to the next with no success. So, when the playlist ends, I've got a stupid message saying that the sound device is busy. But it's not!

What am I doing wrong? I know there must be a very basic solution to this.

Thanks.

---

### Post by thunderduck3141 on 2006-06-28
u need alsamixer

---

### Post by Marcos.Rufino on 2006-06-28
[QUOTE=thunderduck3141]u need alsamixer[/QUOTE]

I've already have it and it doesn't make any difference.

---

### Post by thunderduck3141 on 2006-06-30
hmmm
do you have alsamixer working on your in-use card?
do you have more than one card/onboard sound device

---

### Post by Marcos.Rufino on 2006-07-01
[QUOTE=thunderduck3141]
do you have alsamixer working on your in-use card?
do you have more than one card/onboard sound device[/QUOTE]

Yes, I've got alsamixer working fine in my onboard sound device. I don't have any other sound device.

---

### Post by ender542 on 2007-06-18
I found a similar problem that had a posted solution:
[kaffeine block /dev/dsp]("http://ubuntuforums.org/showthread.php?t=341846")

---

### Post by Geekkit on 2007-06-18
> **ender542 said:**
> I found a similar problem that had a posted solution:
[kaffeine block /dev/dsp]("http://ubuntuforums.org/showthread.php?t=341846")

There's also Sound Preferences for Gnome which works too.  :)

---

