---
title: "how to create a startup launcher for alsa settings"
date: 2012-01-05
forum: General Help
---

### Post by doron387 on 2012-01-05
Hi,
I have a sound problem on my Gigabyte w566u Intel core2duo laptop.
the recorder does not work unless I :
open terminal,
type alsamixer
change the mic to intenal mic (to do so i have to use TAB to jump to the next page, and arrow keys to go to the mic column and use the up/down arroes to choose internal mic)
the problem is that the settings in alsa are going back to default after reboot and I need these settings in order to use the applications>sound&video>Recorder and in order to talk in Skype without having to connect the headphones + speaker set.
I am using ubuntu 10.10 64-bit.
I have tried all kinds of methods to save alsamixer's settings but non of them worked after reboot so i wish to create a script that will run automatically on startup and do all these actions(and i have done so just once, some 2 years ago, accompanied by very accurate instructions from the forum, i don't know to do it by myself).
is it possible ? (though, i am sure that finding the way to save alsamixer's settings must be easier but it seems that nobody knows how to do it - my post was watched 72 times, and replied 0 times.)
thanks
doron387

---

### Post by Basher101 on 2012-01-05
if you can do everything you listed with commands, you can insert the sequency of commands to the file /etc/rc.local

there is at the bottom a line with```
EXIT
```
you paste any command you want to be executed at startup **_above_** that line.

if some things cannot be done by commands you must create a script and apply settings so that it gets executed at startup..

p.s. i have no expirience with scripts at all. All i know is that it has to be a Bash script. You can either google how to make those or ask someone to make one for you..

---

