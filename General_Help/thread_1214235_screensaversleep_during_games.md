---
title: "screensaver/sleep during games"
date: 2009-07-15
forum: General Help
---

### Post by DigitalWolf333 on 2009-07-15
i've had ubuntu for 3 days now and i have a problem...

while playing games for a while the game would suddenly go into windowed and i would have to click the game in the window list to put it back and keep playing. i eventually realized the screensaver was causing this.

apparently it doesn't realize i'm using the computer when i'm playing games at full screen.

i had an event yesterday when i was playing urban terror where the screen saver came up then the computer went to sleep and i couldn't recover it cause the game was up...i had no choice but to hold the power button down to shut down...

i enjoy the screensaver and i need the sleep timer on cause i often leave the computer alone for hours with out thinking to put it to sleep my self. 

is there some fix for this?
--------------------------------
running ubuntu 9.04

---

### Post by egalvan on 2009-07-15
> **DigitalWolf333 said:**
> 

i enjoy the screensaver and i need the sleep timer on cause[B] i often leave the computer alone for hours with out thinking to put it to sleep my self. 
[/B]
is there some fix for this?


Note: this is not a fix... I don't know what causes this problem, and don't know the fix...

But,
You could run folding@home or a BOINC project, and lend some help in solving some worthwhile problem?

One thing to be aware of: not all of these projects work nicely with screen savers... bummer if you like your screenie

---

### Post by NightwishFan on 2009-07-15
Try disabling compiz before you play a game. There is a handy tray for doing this in the repos. (Fusion icon?) I remember in the old days (around gutsy), I switched to KDE because my games kept unwindowing and crashing, I did not think Compiz was the problem. (Which it was). Well thanks to knowing that I can use GNOME in peace. Please note that Compiz does not play nicely with OpenGL applications, they may be a bit slower or odd. For the majority of games you may not notice, especially if you have a great graphics card.

---

### Post by CatKiller on 2009-07-15
> **NightwishFan said:**
> Please note that Compiz does not play nicely with OpenGL applications, they may be a bit slower or odd. For the majority of games you may not notice, especially if you have a great graphics card.

Actually, although I got horrible performance in OpenGL applications when I first started using Compiz (actually, it was Beryl then, before the merge) it's not been a problem for me for quite some time. My graphics card really doesn't count as "great" - it's just a GeForce 6200, but the problems got fixed while I was still using a GeForce 2 GTS. You might want to try toggling the Unredirect Fullscreen Windows option in CCSM.

For the OP: One solution would be to turn the screensaver off as you launch the game. The key you probably want to change is /apps/gnome-screensaver/idle_activation_enabled. It's possible to change this from the command line with gconftool (although I can never remember exactly how) which means that you could run the command to disable the screensaver, followed by the command to launch the game, followed by the command to re-enable the screensaver again when you're done. Once you've established that your chained command works as expected you can modify your launchers to run that command instead of just the command to launch the application.

---

### Post by DigitalWolf333 on 2009-07-15
but the sleep fuction (which is slightly more important) needs to be turned off as well, what would be the script to that?

----------------------------------------
hm, would it be possible to bind the setting to a key combination?

i think compiz can do that...

simply hit a button combo to turn it off and one to turn it on...

---

### Post by CatKiller on 2009-07-16
As I understand it, the GConf key I listed above stops the computer signalling that it's idle at all, which means that whatever the time limit is between the idle signal being sent and the computer hibernating it will never happen because the signal is never sent. Feel free to look around in gconf-editor for other values that might interest you though.

---

### Post by NightwishFan on 2009-07-16
There is a GNOME panel applet for quickly inhibiting power management. You may find that useful. It will show you whether it is inhibited or not graphically. 

As for OpenGL performance, it was poor in the past, but better now. There is still a slight reduction, and some apps do not play nice with it. The undirect fullscreen windows is a good tip. For me it removes flickering in fspot and movie players. Having it on does not seem to improve performance anywhere. Good luck!

---

### Post by DigitalWolf333 on 2009-07-18
i solved the computer sleep problem, turns out theres something i can add to the panel to inhibit power saving, it seems to work sofar. thanks for the help!

---

### Post by morrie on 2009-10-12
This is the same problem that I read about in Dapper; there's still no quick-fix?

Can any of you hit me with some specificity as to how to achieve any of these solutions?  I've tried to find the things you are talking about, but I don't have enough info??

What is Compiz and how do I disable it? 
Found a cool script, but no idea how to use it...


And what about the Gconf key?  How and what do I do to use this to solve the problem?


"I found the thing and fixed it" doesn't help anyone.  Digital Wolf, would you like to please share how you did what?

Thanks

---

### Post by PrePenguin on 2009-10-12
sudo apt-get install ubuntu-restricted-extras
 
 
Scroll to compiz in program manager

---

### Post by morrie on 2009-10-12
This is the same problem that I read about in Dapper; there's still on quick-fix?

Can any of you hit me with some specificity as to how to achieve any of these solutions?  I've tried to find the things you are talking about, but I don't have enough info??

What is Compiz and how do I disable it? 
Found a cool script, but no idea how to use it...


And what about the Gconf key?  How and what do I do to use this to solve the problem?


"I found the thing and fixed it" doesn't help anyone.  Digital Wolf, would you like to please share how you did what?

Thanks,

---

### Post by morrie on 2009-10-12
For anyone else who read this post.  I found this, as the quick fix (haven't tried it yet, but it looks promising)...


It's called "compiz switch":
[http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)


Cheers

---

