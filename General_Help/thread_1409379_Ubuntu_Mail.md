---
title: "Ubuntu Mail"
date: 2010-02-17
forum: General Help
---

### Post by altjx on 2010-02-17
I know I've probably should've searched a little harder than what I already did but... If evolution mail is closed, I get no notifications... How can I minimize this to the tray, or have the notifications show even with the program closed?

---

### Post by darolu on 2010-02-17
There is a plugin to do this; open a terminal and install with:
```
sudo apt-get install evolution-plugins
```
You can also try with:
```
sudo apt-get install mail-notification-evolution
```

---

### Post by altjx on 2010-02-17
> **darolu said:**
> There is a plugin to do this; open a terminal and install with:
```
sudo apt-get install evolution-plugins
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
evolution-plugins is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.

```

Doesn't look like anything happened, lol.

---

### Post by philinux on 2010-02-17
> **altjx said:**
> I know I've probably should've searched a little harder than what I already did but... If evolution mail is closed, I get no notifications... How can I minimize this to the tray, or have the notifications show even with the program closed?

Install

mail-notification-evolution

From synaptic or terminal.

Or use the app.

alltray

---

### Post by altjx on 2010-02-17
> **philinux said:**
> Install

mail-notification-evolution

From synaptic or terminal.

Or use the app.

alltray

K, I just installed mail notification for evolution. I closed the evolution mail program out. I'm not sure if it's working or not, did I have to configure anything?

---

### Post by darolu on 2010-02-17
I just tried them all, including [alltray]("http://alltray.trausch.us/") and none of them work at all. I have no idea why; not even the indicator applet that comes bye default in karmic works.
I don't know if Thunderbird has a working plug in that does what you want.

---

### Post by altjx on 2010-02-17
> **darolu said:**
> I just tried them all, including [alltray]("http://alltray.trausch.us/") and none of them work at all. I have no idea why; not even the indicator applet that comes bye default in karmic works.
I don't know if Thunderbird has a working plug in that does what you want.

Oh ok, thought it might've been just me, lol

---

### Post by altjx on 2010-02-17
Anyone got any other suggestions?

---

