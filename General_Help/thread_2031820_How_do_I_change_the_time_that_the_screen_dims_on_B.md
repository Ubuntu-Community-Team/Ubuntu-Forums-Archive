---
title: "How do I change the time that the screen dims on Battery"
date: 2012-07-22
forum: General Help
---

### Post by irv on 2012-07-22
When I am running on battery and reading, my screen dims in 30 seconds. I would like to increase this time, but can find where to do this.
There is a place to turn the dim off, but I would like to leave it on but change the time before it dims.
[ATTACH]221635[/ATTACH]

---

### Post by irv on 2012-07-26
I guess there must not be a way to do this? Three days and no reply.

---

### Post by drs305 on 2012-07-26
I'm not on a laptop but check System Settings (upper right button on 12.04)> Power.

---

### Post by irv on 2012-07-26
> **drs305 said:**
> I'm not on a laptop but check System Settings (upper right button on 12.04)> Power.
I don't see any buttons on the Power settings in System Settings?
[ATTACH]221839[/ATTACH]   [ATTACH]221840[/ATTACH]

---

### Post by irv on 2012-07-26
OK, I found the answer on [askubuntu]("http://askubuntu.com/questions/98184/increase-screen-idle-dim-timeout").
```
gsettings set org.gnome.settings-daemon.plugins.power idle-dim-time 60
```
But just like person who posted the remark I would ask the same question. 
> I'm absolutely comfortable using the terminal (and this worked great for me by the way), but I sure do wish Ubuntu 11.10 let me change these kind of things through the "System Settings" GUI... &#8211; b.long Feb 17 at 0:01
There's no reason this shouldn't be configurable through the GUI settings. &#8211; Thucydides411 Jul 23 at 16:16
But I would add it never got put in in 12.04 either.
EDIT: I will mark this thread solved because I added it to Ubuntu Brainstorm.

---

