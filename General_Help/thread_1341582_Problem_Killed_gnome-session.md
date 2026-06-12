---
title: "Problem: Killed gnome-session"
date: 2009-11-29
forum: General Help
---

### Post by Happyman7 on 2009-11-29
'Owdy,

Ok, today I was messing around and just being me and I right-clicked on the "Applications" area of the top panel. 
[IMG]http://img6.imageshack.us/img6/8431/prbfxscrnsht.jpg[/IMG]
and I clicked "Remove from Panel" and then the "Applications," "Places," and "System," menus disappeared. I panicked (which is unusual for me, I don't even know why I did) and I brought up terminal and typed "Kill" and then the process ID for gnome-session (I Killed gnome-session). So after 1 or 2 (maybe 3) seconds  the screen turned black and then brought up what closely resembled a full-screen terminal, which operated exactly the same as terminal, that I couldn't escape from. So basically I was smack-dab helpless in front of a screen that does nothing but terminal stuff.


[B]How do I fix this?
and, if possible, how do I get my menus back?

[/B]I'm using Ubuntu Karmic Koala (9.10) on a Dell XPS 410 computer. Ubuntu is installed _inside_ of Windows XP
Thanks is advanced :)

---

### Post by Happyman7 on 2009-12-01
Is anyone going to answer this?

---

### Post by mo.reina on 2009-12-01
have you tried a reboot?  killing X is no big deal, it will reload on reboot, or if you type:

```
/etc/init.d/gdm start
```

---

### Post by BandD on 2009-12-01
So you used WUBI?  I haven't used WUBI at all, but a simple restart should work.  You can do that by issuing either:
```
sudo shutdown -r now
```

or

```
sudo reboot
```

from the command line, they produce the same effect.  Gnome session should restart without issues.  You might also be able to get back your gnome-session by issuing 
```
sudo /etc/init.d/gdm restart
```
I haven't really played around with killing gnome-session before.  

You can get the "Applications" et al back by simply clicking on a blank space within the top panel and select "add to panel" and then scroll down to "Menu Bar" and click add.  Voila!  It should be back.

---

