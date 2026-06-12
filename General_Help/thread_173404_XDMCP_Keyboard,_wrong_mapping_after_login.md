---
title: "XDMCP Keyboard, wrong mapping after login"
date: 2006-05-10
forum: General Help
---

### Post by OzPhoenix on 2006-05-10
Hi,

I have the following setup:
- x86 machine running Ubuntu
- x86 machine running Windows XP
- PowerBook running Mac OS X 10.4

When I connect to my Ubuntu machine via XDMCP from my Mac, I am able to login with no issues. However after successfully loging in and getting to the gnome desktop, my keyboard mapping seems to be all messed up. If I type j I get l, if I type k I get ',' and if I try keys on the left of the keyboard no character comes up, but I get a beep for each key press.

However, when I connect to my Ubuntu machine from XP, everything works as expected. When I connect to my Ubuntu machine via SSH from the Mac everything works as expected. If I connect from the Mac via ssh -X and then launch an xterm, it works as expected. And as stated, the initial login panel allows me to type in my username and password with no issues.

So it seems that Login panel (is that GDM?) is fine, but the desktop (which I think is Gnome?) seems to swap the keyboard mapping/layout around.

I've tried using the Keyboard Preferences and Keyboard Layout Switcher. However when I'm in a XDMCP session from the Mac, the 'keyboard model' comes up as "Unknown". Further, when I browse for another model, none come up in the list. But when I do the same thing from my XP machine, there are heaps of different models to choose from (why don't they show up in the Mac XDMCP session?).

Regards,
Oz.

P.S. I've also seen all the threads about num-lock, but that doesn't seem to be it. I can actually turn num-lock on and off and it has an effect on the keys that double as the keypad (remember this is a laptop keyboard). But even those are not coming up correctly, just differently.

---

### Post by DeepBlade on 2007-07-22
I have the same problem. Can anyone help??

---

### Post by ivotedforkodos on 2007-08-21
I also have the same problem. See this thread:

[http://ubuntuforums.org/showthread.php?t=299916&page=2](http://ubuntuforums.org/showthread.php?t=299916&page=2)

Also, Oz, what are you using to connect to the Ubuntu machine from Windows?

---

### Post by OzPhoenix on 2007-08-21
When I originally posted this I was using the X package within cygwin. But lately I've started using Xming. It works just as well, but I started to use it as it was easy to explain to others at work.

---

### Post by ivotedforkodos on 2007-08-22
Right. Well these two threads are the same issue, I think:

[http://ubuntuforums.org/showthread.php?t=299916](http://ubuntuforums.org/showthread.php?t=299916)
[http://ubuntuforums.org/showthread.php?t=396308](http://ubuntuforums.org/showthread.php?t=396308)

Following the latter, I tried the "-kb" option, but it didn't seem to have much of an effect. Once I was logged into the Ubuntu machine, I tried changing the keyboard layout using the "Keyboard" preferences pane, and that DID have an effect on the layout of the keyboard. However, there are several dozen possible layouts and I have no idea which one is likely to work, or even if one of them will work. But, I suppose you could try all of the possibilities.

---

