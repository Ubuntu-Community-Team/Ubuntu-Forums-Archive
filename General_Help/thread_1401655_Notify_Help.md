---
title: "Notify Help?"
date: 2010-02-08
forum: General Help
---

### Post by jeff.sadowski on 2010-02-08
I would like to know if I can setup notify to ignore some stuff but not others. I like seeing the volume and screen brightness information. I don't mind emergency battery information also. However when I am on a flaky network I do not want to see connected, disconnected, connected, disconnected, ... all the time it is irritating especially since I see it via the status icon in the systray and the status icon is more up to date.

The only documents I could find from google either disable notify completely or tell what notify does like so
[https://wiki.ubuntu.com/NotifyOSD#Bubble%20appearance%20and%20layout](https://wiki.ubuntu.com/NotifyOSD#Bubble%20appearance%20and%20layout)

---

### Post by feistybill on 2010-02-10
> **jeff.sadowski said:**
> I would like to know if I can setup notify to ignore some stuff but not others. I like seeing the volume and screen brightness information. I don't mind emergency battery information also. However when I am on a flaky network I do not want to see connected, disconnected, connected, disconnected, ...

I was looking for an answer to this exact same question...

Is there a way to configure Ubuntu's notification system? Someone please reply... the only other possibility is uninstall the OSD completely.

---

### Post by BOFH+ on 2010-02-10
There are a few patches here: [http://ubuntuforums.org/showthread.php?t=1378676](http://ubuntuforums.org/showthread.php?t=1378676)

The patches only allow customizing colors and position of the popup, nothing more ATM.

---

### Post by patchwork on 2010-02-10
I think this is what you are looking for, though I'm not sure if this will disable the pop-up notification or the wifi-indicator.    You may also need to restart X before the settings take place, not sure.

From the terminal

```
gconf-editor
```Click on apps > nm-applet 
then click on each of the following:
disable connected notifications
disable disconnected notifications

---

### Post by jeff.sadowski on 2010-02-11
> **patchwork said:**
> I think this is what you are looking for, though I'm not sure if this will disable the pop-up notification or the wifi-indicator.    You may also need to restart X before the settings take place, not sure.

From the terminal

```
gconf-editor
```Click on apps > nm-applet 
then click on each of the following:
disable connected notifications
disable disconnected notifications

This didn't do anything that I can see it still pops up bubbles that look like it is coming from notify. Maybe there is another place in gconf-editor for it. I even rebooted after making the change maybe its comming from an underlying program controlling the wireless?

Ok my eeepc is now working 99.99999 % the way I want it I can live with a notify bubble for this. I will just turn wireless off in places I'm not using it. It will save on power as well. Yeah notify isn't really the problem its the programs reporting to it. It could be nm-applet is at fault in its configuration.

---

