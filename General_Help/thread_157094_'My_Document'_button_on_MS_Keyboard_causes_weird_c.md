---
title: "'My Document' button on MS Keyboard causes weird crash"
date: 2006-04-08
forum: General Help
---

### Post by s|k on 2006-04-08
Hi, the 'My Document' button that came with my Microsoft keyboard will crash the computer, cause it to completely shut down, and when I try to reboot into Ubuntu it sends me into the Bios, and then after rebooting again it freezes, and finally on the third reboot everything is working again.

What's causing this and how do I disable that button? My cat jumped on it.

Thanks.

---

### Post by Sef on 2006-04-08
> how do I disable that button?

System > Preferences > Keyboard shortcuts.  

See if you can disable it there.

---

### Post by s|k on 2006-04-08
[QUOTE=Sef]System > Preferences > Keyboard shortcuts.  

See if you can disable it there.[/QUOTE]
No I've tried. I tried to set it to something else, like 'run a terminal' but after I get out of keyboard shortcuts and hit it, everything grashes and the computer shuts off.

Interestingly, when in keyboard shortcuts I can hit it and it wont crash the system. The value of the button is 0xef

Any other suggestions? I think this is a huge bug in gnome or linux or something.

---

### Post by jstad on 2006-04-18
I have the same problem. I have the Microsoft Wireless Elite Keyboard.

---

### Post by dmizer on 2006-04-18
you might get away with using this technique to change the key code from the shell.  it's a different problem in this thread, but since you know the keycode, you can just reset it to something a bit more mundane than your current "auto crash" setting.

[http://ubuntuforums.org/showthread.php?t=119449&highlight=unknown+key+dmesg](http://ubuntuforums.org/showthread.php?t=119449&highlight=unknown+key+dmesg)
edit to include the more direct url for the change ...
[http://ubuntuforums.org/showthread.php?t=119499]("http://ubuntuforums.org/showthread.php?t=119499")

oh what the heck ... i'll just past the instructions here.  direct from dcstar himself:
```
setkeycodes e02a 256 
sudo /etc/init.d/hotkey-setup restart

```
just change "e02a" to your problem key code (0xef)

---

### Post by Face1 on 2006-04-18
If worst comes to worst, you can always crack open the keyboard and physically disable the key (like with a knife :D).  But that's a waste of a perfectly good option key.

---

### Post by pwrstick on 2006-04-18
Install Windows?

*I keed I keed*

---

### Post by pellgarlic on 2006-05-18
a "microsoft" keyboard?... the offending button is probably hard-coded to crash any other operating system you try to use it on!

i'd also be suspicious of your cat, and watch for signs that it is a saboteur sent by bill gates' minions ... does it spend a lot of time looking out of the window (tm)?...

---

