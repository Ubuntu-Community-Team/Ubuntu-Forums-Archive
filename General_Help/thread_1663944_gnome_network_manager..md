---
title: "gnome network manager."
date: 2011-01-10
forum: General Help
---

### Post by Drenriza on 2011-01-10
In my top bar (where i also have the, bluetooth, sound time and date and so on icons) i have lost my icon to manage my network. Wired, wireless and VPN. How do i get it back?

Thanks on advance.
Kind Regards.

---

### Post by powertower on 2011-01-10
I think this indicates your Network Manager is no longer managing the network adapters. I don't think their is an easy drag / drop way to add icons back to the "Indicator Applet". You need to find out why network manager is not managing your connections...

---

### Post by 0N3 on 2011-01-10
Right click your panel on an empty space and selct add to panel and add indicator-applet

---

### Post by Drenriza on 2011-01-10
> **0N3 said:**
> Right click your panel on an empty space and selct add to panel and add indicator-applet

I tried to do so. But i only got bluetooth, sound and the mail icon. I did not get the network manager icon.

> I think this indicates your Network Manager is no longer managing the  network adapters. I don't think their is an easy drag / drop way to add  icons back to the "Indicator Applet". You need to find out why network  manager is not managing your connections... 	

Yesterday when i started my pc, i got an warning saying that the desktop theme codent load properly because a program had done some error. I than got the dialog box

Do you want to delete the program who was the error to the theme not loading
yes / no. By ACCIDENT! i hitted yes or delete. And now i cannot see the icon.

I dont know if it was this icon. Because the message did not say, but its pretty convinient that it disappear as i hit delete.

---

### Post by Drenriza on 2011-01-11
This is quite a problem. Anyone know how i can manage my VPN connections without the network manager icon?

Or get the icon back?

> I think this indicates your Network Manager is no longer managing  the  network adapters. I don't think their is an easy drag / drop way  to add  icons back to the "Indicator Applet". You need to find out why  network  manager is not managing your connections...     How do i find out the above?

EDIT.
I found out that the command to start the applet is
```
nm-applet --sm-disable
```is this correct or does it need to be something else. The disable is what i notice, should that be enable?

EDIT2
```
cristian@cristian-Znote:~$ nm-applet
Et eksemplar af panelprogrammet til netværkshåndtering kører allerede.

** (nm-applet:3901): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.
```

---

### Post by Drenriza on 2011-01-11
Solved.

Needed to right click the top panel. And add, status field. Which contained the network manager icon.

---

