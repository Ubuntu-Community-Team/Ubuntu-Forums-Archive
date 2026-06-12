---
title: "Considering a Down-Grade 10.04 to 9.04"
date: 2010-12-10
forum: General Help
---

### Post by Legeril on 2010-12-10
So even though I am a new user to Ubuntu and Linux in general, I made the swap because of the promise of security, user friendliness and flexibility / customisation ability.

The first two points have been achieved perfectly and flawlessly.. Though I have found Ubuntu 10.04 laking the ability to customise my environment the way I was promised, even 90% of the themes I try to download are not compatible with the current GDM. And I wont start with the log-in screens etc.

I have been told that the loss of this customisation started with 9.04 so I am considering down-grading to Karmic Koala to see how I like it.

What are peoples views on this? Are there points I am over looking here? How did 9.04 fair as an OS? What will I lose from the down-grade? Or have I just completely just over looked my ability to customise 10.04?

I am not a computer genius, in case you haven't guessed :D

---

### Post by argedion on 2010-12-10
This may help you instead of doing a down grade.

Add the repository,
```
sudo add-apt-repository ppa:tualatrix/ppa
```

Update your repository,
```
sudo apt-get update
```

Install ubuntu-tweak
```
sudo apt-get install ubuntu-tweak
```

Thanks to the guys wilee-nilee and karthick87 for this one.

This is a tweak program that will give you a bit more control over your system. May not be everything you want but a big part of switching OS's is the learning curve. I would not be so quick to "down grade" The System is fully customizable its just a matter of learning how. Thats why you have to make the forums one of your best friends. Hope this helps you out any ways. 
Happy Computing

---

### Post by Legeril on 2010-12-10
Hey thanks a lot, I do have Tweak installed already. It seems to make things more easy to find yes, but I am still not able to over-haul complete styles or configure things like the log in screen to look any different.

---

### Post by a-user on 2010-12-10
gdm2 is not themeable. the only thing you can do is change the background image and theme of the login dialog.

to do this open a terminal and do:
gksudo -u gdm gnome-control-center

alternatively you can try this (untested):
[http://maketecheasier.com/gdm2-setup-reclaim-control-of-your-login-in-ubuntu-lucid/2010/05/20](http://maketecheasier.com/gdm2-setup-reclaim-control-of-your-login-in-ubuntu-lucid/2010/05/20)
or this:
[http://www.ubunturoot.com/2010/08/custimize-login-screen-on-ubuntu-gdm2.html](http://www.ubunturoot.com/2010/08/custimize-login-screen-on-ubuntu-gdm2.html)

---

### Post by oldos2er on 2010-12-10
> **Legeril said:**
> What are peoples views on this? 

9.04 reached its end-of-life in October, which means no more updates, offline repositories.

---

### Post by cyberphrog on 2010-12-10
I found that 10.04 was better with certain pieces of hardware (e.g., specific printers, graphics cards) than 9.04.

---

### Post by Legeril on 2010-12-11
OK guys, thanks for all your opinions and insight. I guess I'll have to stay put for now, but it's not so bad when all is said and done everything still looks better than windows :)

marking thread closed

---

