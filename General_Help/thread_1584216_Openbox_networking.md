---
title: "Openbox networking"
date: 2010-09-28
forum: General Help
---

### Post by zigmo on 2010-09-28
When I started a lubuntu session, the first time, I had to connect to my wireless network. Every time after that, wicd connected automatically.
When I run an openbox session, I'd automatically connect to my wireless network.
If I ever went anywhere else, I'd have to run a lubuntu session first to connect to the new network and then I could connect in openbox.
I just upgraded to 10.04 (I was running 9.04) and now I can't connect to my wireless network in openbox at all.
I tried to run wicd manually in openbox, but it never came up.
Any suggestions as to how to get network access in openbox would be appreciated.
Thanks.

---

### Post by mikewhatever on 2010-09-28
You need a network manager of some kind, wicd, gnome nm, doesn't matter. Perhaps the upgrade didn't go well. Is upgrading from 9.04 to 10.04 supported?

---

### Post by zigmo on 2010-09-28
Yeah - I know.
I've got wicd running. In fact, when I'm in openbox, I can run
```
ps - A | grep wicd*
```
and see that wicd and the wicd-client are both running. I just can't seem to access them in any way. Running wicd or wicd-client again from the command line doesn't do anything except bring up another instance of each.
Still, wicd is working fine during an LXDE session - just no longer with openbox.

---

### Post by bodhi.zazen on 2010-09-28
I think you need some kind of a panel for wicd to run in. Openbox has no panel and no notification area, LXDE is Openbox + a (LXDE) panel.

---

### Post by zigmo on 2010-09-29
I never needed one before and it's still running. Even so - if I have to add a panel now that I upgraded to get it to work, I'll do it.
I guess the next question is - how do I add a panel? Is it just a package I can load? If so, what's a simple, low memory one I can use.

---

### Post by bodhi.zazen on 2010-09-29
> **zigmo said:**
> I never needed one before and it's still running. Even so - if I have to add a panel now that I upgraded to get it to work, I'll do it.
I guess the next question is - how do I add a panel? Is it just a package I can load? If so, what's a simple, low memory one I can use.

Yes, there are several options.

I would tend to suggest lxde as it is probably the most popular at the moment.

I used pypanel in the past 

See also : 

[http://wiki.archlinux.org/index.php/Openbox#Panels.2C_trays.2C_and_pagers](http://wiki.archlinux.org/index.php/Openbox#Panels.2C_trays.2C_and_pagers)

---

### Post by TheDexter1111 on 2011-03-30
> **zigmo said:**
> Yeah - I know.
I've got wicd running. In fact, when I'm in openbox, I can run
```
ps - A | grep wicd*
```and see that wicd and the wicd-client are both running. I just can't seem to access them in any way. Running wicd or wicd-client again from the command line doesn't do anything except bring up another instance of each.
Still, wicd is working fine during an LXDE session - just no longer with openbox.


for wicd UI in openbox run:

$ wicd-client -n

To run in terminal run:

$ wicd-curses

if you dont have curses installed do:

$sudo apt-get install wicd-curses

---

### Post by lithopsian on 2011-03-30
Yes, lots of ways to skin a cat.  A common panel with Openbox is Tint2.  You can use Wicd with this and lots of people do.  I use nm-applet which is very straightforward when it works straight out of the box, but perhaps more of a pain than Wicd when it doesn't.

---

