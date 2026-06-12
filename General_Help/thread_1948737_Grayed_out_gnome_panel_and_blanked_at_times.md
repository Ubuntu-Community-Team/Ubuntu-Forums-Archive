---
title: "Grayed out gnome panel and blanked at times"
date: 2012-03-28
forum: General Help
---

### Post by jfreak53 on 2012-03-28
I am using ubuntu 11.04.  I have a problem that I think is related to the graphics driver's but I'm not sure really.

Every couple days when I start up the computer instead of the blackish default gnome theme I get the ugly old grey theme on everything.  It have to restart GDM a few times and log back in to get it to go back, sometimes it's a matter of restarting the PC.

Then everytime I get a notification from an app in my bar, the same apps I use on my laptop without problem's, when the notification comes up it blank's out my top panel completely!  I mean makes it transparent.  I have to hover over icons and click on the menu's to get it back.

I kind of figure it's something with the graphics driver but I don't have a clue how to fix it.  I have ZERO additional driver's installed, all default.

Any thoughts?

---

### Post by jfreak53 on 2012-03-29
Any thoughts?  Attached is a screenshot of what it does.

[IMG]http://i.imgur.com/atgaW.jpg[/IMG]

---

### Post by skatinjj on 2012-03-29
What graphics card are you using?  If you do not know you can find out by running this from the terminal:

```
lspci
```

And looking for the line with VGA.

---

### Post by jfreak53 on 2012-03-29
Graphics Adapter:

> 01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

---

### Post by skatinjj on 2012-03-29
Do you have any desktop effects turned on?  If so, I would just turn them off.  Also, you can read this.

[http://ubuntuforums.org/archive/index.php/t-1241800.html]("http://ubuntuforums.org/archive/index.php/t-1241800.html")

---

