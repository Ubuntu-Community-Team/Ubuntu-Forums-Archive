---
title: "help - my computer won't start up"
date: 2010-04-27
forum: General Help
---

### Post by arexen on 2010-04-27
I am a newbie. I screwed up somehow..
I recently upgraded from 9,04 to 9,10. Don't know if that makes any difference.

This happened:
I installed 3 compiz applications, don't remember the exact names, (I'm obviously not writing from my own computer) something with python-compiz? ...*plugin and a third one - don't remember the name. (i saw a guide on youtube, that i can't find now).
As I applied changes to my desktop via compiz, it froze completely. I could't do anything but turn it off. Next time it startet up, it froze just before finish starting up.

I tried deleting some of the compiz stuff (there is a lot more then i installed) using recovery mode (kernel 2.6.31.20) and comand 'aptitude remove' I figured that might help - it didn't.
I can start the computer in kernel 2.6.28.18 but the mouse doesn't work. i can't figure out how to get into add/remove or synaptic package.. without a mouse...

Does anyone have a sugestion on what i should do? i'd love to avoid loosing my data...

---

### Post by mörgæs on 2010-04-28
You can do all package management from the command line. Add/remove, Synaptic and Software Centre are just skins. 

Some of the main commands are here:
[https://help.ubuntu.com/8.04/serverguide/C/apt-get.html](https://help.ubuntu.com/8.04/serverguide/C/apt-get.html)

It is good to run apt-get clean before apt-get update.

---

### Post by lordbux on 2010-04-28
> **arexen said:**
> I am a newbie. I screwed up somehow..
I recently upgraded from 9,04 to 9,10. Don't know if that makes any difference.

This happened:
I installed 3 compiz applications, don't remember the exact names, (I'm obviously not writing from my own computer) something with python-compiz? ...*plugin and a third one - don't remember the name. (i saw a guide on youtube, that i can't find now).
As I applied changes to my desktop via compiz, it froze completely. I could't do anything but turn it off. Next time it startet up, it froze just before finish starting up.

I tried deleting some of the compiz stuff (there is a lot more then i installed) using recovery mode (kernel 2.6.31.20) and comand 'aptitude remove' I figured that might help - it didn't.
I can start the computer in kernel 2.6.28.18 but the mouse doesn't work. i can't figure out how to get into add/remove or synaptic package.. without a mouse...

Does anyone have a sugestion on what i should do? i'd love to avoid loosing my data...

just press Alt+f2
then enter ```
gksu synaptic
```
press enter
use TAB to control the interface

---

### Post by P4man on 2010-04-28
or try turning compiz off: alt F2 and then type

```
metacity --replace
```

might fix the mouse if it was a compiz plugin that killed it.

If you cant get it fixed, you can check your log and tell us exactly what you installed. Its in /var/log/dpkg.log

to view it

```
cat /var/log/dpkg.log
```
or to view it in text editor

```
nano /var/log/dpkg.log
```

or copy it to a usb stick so you can post it here:

```
cp /var/log/dpkg.log /media/*yourusbstick*
```

replace yourusbstick with the actual path to your stick. If you dont know, type the first part (/media/) and press TAB key to complete or view a list of possibilities.

Messing up your ubuntu is a great way to learn!

---

### Post by arexen on 2010-05-06
Thanks for the help! I found another thread about the same problem (it was the reflection effect that messed it up).

---

