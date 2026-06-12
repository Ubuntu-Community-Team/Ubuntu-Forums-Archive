---
title: "Can you get rid of?"
date: 2011-11-28
forum: General Help
---

### Post by Sheeppy on 2011-11-28
Can you get rid of the Tool bar thing? I'm trying to make Ubuntu look like a Mac layout so I want to get rid of it.
Please Help :D <3

---

### Post by Derek Karpinski on 2011-11-28
Assuming Ubuntu 11.10 and you want to get rid of the menu bar (unity launcher) on the left of the screen:

Log off, click on the 'gear' by your log in name, choose 'GNOME classic', go to software center, and search for 'GLX-Dock (Cairo-Dock with Open GL) and install it.  Configure the dock to look like mac.

:D

---

### Post by Sheeppy on 2011-11-28
Wow
1) thank you!
2)Thank you for posting so fast!
3)I feel like I derp hardcore lmao <3

---

### Post by Sheeppy on 2011-11-28
> **Derek Karpinski said:**
> Assuming Ubuntu 11.10 and you want to get rid of the menu bar (unity launcher) on the left of the screen:

Log off, click on the 'gear' by your log in name, choose 'GNOME classic',

:D
 
I don't see the GNOME classic setting when I log off

---

### Post by Derek Karpinski on 2011-11-28
Which version of Ubuntu are you running?

What options show up when you click the gear icon on the login screen?

Again, assuming 11.10, press 'ctrl-alt-T' and type, or copy paste:

```
sudo apt-get update
```

Then:

```
sudo apt-get install gnome-shell
```Reboot, then you should have 'GNOME classic' option.

[IMG]http://www.virtualhelp.me/images/stories/ubuntu_11.10_login_sm.jpg[/IMG]

Edit: That will install gnome-shell......along with gnome classic.  You could save space and just install gnome-classic.

```
sudo apt-get install gnome-session-fallback
```

---

### Post by the_windwalker on 2011-11-28
> **Derek Karpinski said:**
> Assuming Ubuntu 11.10 and you want to get rid of the menu bar (unity launcher) on the left of the screen:

Log off, click on the 'gear' by your log in name, choose 'GNOME classic', go to software center, and search for 'GLX-Dock (Cairo-Dock with Open GL) and install it.  Configure the dock to look like mac.

:D
Will that give me a screen that looks and acts like 10.10?  I found that upgrading to 11.04 was a mistake, then I went to 11.10.  Now, I'm ready to wipe the hard drive and reload 10.10.  Faster and MUCH easier to navigate.

---

### Post by Derek Karpinski on 2011-11-28
> **the_windwalker said:**
> Will that give me a screen that looks and acts like 10.10?  I found that upgrading to 11.04 was a mistake, then I went to 11.10.  Now, I'm ready to wipe the hard drive and reload 10.10.  Faster and MUCH easier to navigate.

It should.......it won't be exactly the same, but you can get it close.  I use unity, so I can't comment on the accuracy of the instructions of this site:

[http://www.flynsarmy.com/2011/11/how-to-make-ubuntu-11-10-more-usable/](http://www.flynsarmy.com/2011/11/how-to-make-ubuntu-11-10-more-usable/)

---

### Post by Sheeppy on 2011-11-28
> **Derek Karpinski said:**
> Which version of Ubuntu are you running?

What options show up when you click the gear icon on the login screen?

Again, assuming 11.10, press 'ctrl-alt-T' and type, or copy paste:

```
sudo apt-get update
```Then:

```
sudo apt-get install gnome-shell
```Reboot, then you should have 'GNOME classic' option.

[IMG]http://www.virtualhelp.me/images/stories/ubuntu_11.10_login_sm.jpg[/IMG]

Edit: That will install gnome-shell......along with gnome classic.  You could save space and just install gnome-classic.

```
sudo apt-get install gnome-session-fallback
```


I cant get the toolbar things to go away top and bottom I got the dock setup tho

---

