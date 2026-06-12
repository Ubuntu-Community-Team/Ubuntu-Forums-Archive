---
title: "Add System Monitor applet to panel in Ubuntu 12.04"
date: 2012-05-09
forum: General Help
---

### Post by k999 on 2012-05-09
I've just upgraded to Ubuntu 12.04. How do I add applets to the the panel? I like having System Monitor there to keep an eye on what's going on, but I don't see how to add it.

---

### Post by Enigmapond on 2012-05-09
You can't with unity. Use a screenlet or conky.

---

### Post by Peter09 on 2012-05-09
You can add it to the launcher, right click on the icon (when the app is running) and select 'keep in launcher'.

---

### Post by LW7ELK on 2012-05-25
> **k999 said:**
> I've just upgraded to Ubuntu 12.04. How do I add applets to the the panel? I like having System Monitor there to keep an eye on what's going on, but I don't see how to add it.


I installed System Load Indicator 0.2
It's identical to Ubuntu 10.04's
I'm trying to see how to move applets across the top panel now (Why there is no "move" item on menu like before?)

---

### Post by magnetar on 2012-08-07
> **k999 said:**
> I've just upgraded to Ubuntu 12.04. How do I add applets to the the panel? I like having System Monitor there to keep an eye on what's going on, but I don't see how to add it.
Just expanding the solution by "LW7ELK", it is described [here]("http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html"). Basically:

sudo add-apt-repository ppa:indicator-multiload/stable-daily
sudo apt-get update
sudo apt-get install indicator-multiload

Then search for "System Load Indicator" in 'Dash Home' panel and launch it.

---

### Post by Nalin x Linux on 2012-09-26
Press **Alt+Super(window)+Right-click** on Bottom or Top Panel, then click "Add to Panel" then select "System monitor" and click "add"
Good Luck!

---

