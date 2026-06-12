---
title: "Lost apps in top bar"
date: 2011-10-09
forum: General Help
---

### Post by galacticaboy on 2011-10-09
I recently uninstalled Evolution in favor or Thunderbird, when I did my Time and Date in the bar at the top has left me. How can I get that back?

---

### Post by fritz269 on 2011-10-09
You should be able to find the time date in the shortcut menu and make sure the display clock is checked

---

### Post by galacticaboy on 2011-10-09
Where is the Shortcut Menu?

---

### Post by fritz269 on 2011-10-09
click on the ubuntu icon on the left top corner, click on more apps and scroll down

---

### Post by CatKiller on 2011-10-09
It's possible that you've uninstalled the indicator applet. You can re-install it and add it back to the panel, or just add the standard Gnome date and time applet to the panel by right-clicking on it.

---

### Post by galacticaboy on 2011-10-09
> **CatKiller said:**
> It's possible that you've installed the indicator applet. You can re-install it and add it back to the panel, or just add the standard Gnome date and time applet to the panel by right-clicking on it.

I don't use Gnome, I am using Unity and it wont let me right click on it, it does nothing.

> **fritz269 said:**
> click on the ubuntu icon on the left top corner, click on more apps and scroll down

I have done that, there is no shortcuts menu.

---

### Post by CatKiller on 2011-10-09
> **galacticaboy said:**
> I don't use Gnome, I am using Unity and it wont let me right click on it, it does nothing.


You are using Gnome. Unity is Gnome with a Compiz plugin.

I didn't use Unity for very long myself, but ISTR that although a lot of the panel was taken up by the stupid menu bar thing there was still plenty left that you could interact with.

---

### Post by fritz269 on 2011-10-09
I have done that, there is no shortcuts menu.[/QUOTE]

When you click on the icon on the left top corner, it will bring up the apps menu, click on more apps and then clock and calendar. Click on that and make sure the correct box is checked

---

### Post by galacticaboy on 2011-10-09
> **fritz269 said:**
> I have done that, there is no shortcuts menu.

When you click on the icon on the left top corner, it will bring up the apps menu, click on more apps and then clock and calendar. Click on that and make sure the correct box is checked[/QUOTE]

I did that, I have nothing titled Clock, Calendar, Clock and Calendar, or Calendar and Clock, there is nothing there. All I did was uninstall Evolution.

---

### Post by fritz269 on 2011-10-10
Time and date?

---

### Post by galacticaboy on 2011-10-10
> **fritz269 said:**
> Time and date?

Nope, not even Time and Date...

---

### Post by fritz269 on 2011-10-10
I think you must have removed it by accident..not sure how to reinstall it.

---

### Post by Krytarik on 2011-10-11
Make sure the package "indicator-datetime" is installed:
```
sudo apt-get install --reinstall indicator-datetime
```
If it's installed by this command, relogin to make it affect the panel.

Regards.

---

### Post by galacticaboy on 2011-10-11
> **Krytarik said:**
> Make sure the package "indicator-datetime" is installed:
```
sudo apt-get install --reinstall indicator-datetime
```
If it's installed by this command, relogin to make it affect the panel.

Regards.

That worked!!

---

