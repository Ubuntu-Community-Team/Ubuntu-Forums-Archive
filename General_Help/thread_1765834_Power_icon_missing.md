---
title: "Power icon missing"
date: 2011-05-23
forum: General Help
---

### Post by thaDM on 2011-05-23
Hi, I seem to have lost my power icon (even though it is set to "always show" in the settings):

[IMG]http://flamepad.com/img/ScreenshotPowerIcon.png[/IMG]

Anybody have any ideas on getting it back?

---

### Post by thaDM on 2011-05-24
Anybody? It would be really helpful.

---

### Post by wildmanne39 on 2011-05-24
> **thaDM said:**
> Anybody? It would be really helpful.
What ubuntu version and desktop are you running? If it is like gnome classic you can right click on the panel and choose to add an item like power.

---

### Post by thaDM on 2011-05-24
Xubuntu 11.04. It's the indicator applet icon that's missing and I'd like back.

---

### Post by Toz on 2011-05-24
> **thaDM said:**
> Hi, I seem to have lost my power icon (even though it is set to "always show" in the settings):

[IMG]http://flamepad.com/img/ScreenshotPowerIcon.png[/IMG]

Anybody have any ideas on getting it back?

Just to confirm, in the Power Manager settings, is the "Show notifications to notify about the battery state" checked?

---

### Post by thaDM on 2011-05-24
Yes and it is set to "Always Show".

---

### Post by morgengenuss on 2011-05-24
did you remove the notification area (aka systray)?
if you didn't install gnome-power-manager you won't have any power-manager stuff as indicator since xfce4-power-manager only supports systray icons at the moment.

---

### Post by thaDM on 2011-05-24
> **morgengenuss said:**
> did you remove the notification area (aka systray)?
if you didn't install gnome-power-manager you won't have any power-manager stuff as indicator since xfce4-power-manager only supports systray icons at the moment.
The power icon is part of indicator applets: power, wifi, volume. Like this: [http://mogorvamormota.hu/wp-content/uploads/2011/04/xubuntu-natty-desktop.png](http://mogorvamormota.hu/wp-content/uploads/2011/04/xubuntu-natty-desktop.png)
The power one has disappeared.

---

### Post by Toz on 2011-05-24
Perhaps there is a problem with the icon theme. If you change the icon theme, does the battery icon re-appear?

---

### Post by thaDM on 2011-05-24
> **Toz said:**
> Perhaps there is a problem with the icon theme. If you change the icon theme, does the battery icon re-appear?
Well I didn't think this would be it but you're right:
[IMG]http://flamepad.com/img/Screenshot2.png[/IMG]

Strange.

So how do I use elementary dark xubuntu icons then? The icon theme above is too dark.

---

### Post by thaDM on 2011-05-24
Got it! The theme requires the panel to be at least 26px high.

Good spot Toz: I never would have guessed it was simply a problem with the icons!

Cheers.

---

