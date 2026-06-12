---
title: "Frozen &amp; Blank Panels"
date: 2010-03-28
forum: General Help
---

### Post by ChuckT on 2010-03-28
**Please help!**

I was customizing my panels on Gnome desktop and my computer froze when I added two panels on top of each other, so I restarted the pc. Now all I see are blank panels, and when I open a window by clicking an icon on the desktop I see the window but not the top of it (with the X). I rebooted again under a "failsafe" session, but no luck. I cannot right click on the blank panels neither as it won't do anything.

I managed to open my browser by converting a document into an html one and opening it.

I can hear also the fans going crazy, something is running that is overloading my CPU.

I can't open the terminal via the keyboard shortcuts.

I am using Ubuntu 9.10 on a thinkpad X60. 

Thank you very much.

---

### Post by ChuckT on 2010-03-28
up

now nothing is working, i can't even click on icons in my desktop.

i logged in on xterm and opened firefox, can't do anything else?
[B]
any help would be much appreciated... [/B]

can I restore Ubuntu or Gnome Defaults? i do not have a CD. any way to do it via the terminal

---

### Post by guroot on 2010-03-28
You could try to create a new user and logon with it.

```
useradd -m user1
passwd user1
```
Jonathan
[http://www.guroot.com]("http://www.guroot.com?lang=en")

---

### Post by lidex on 2010-03-28
Terminal:
```
gconftool --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by ChuckT on 2010-03-28
> **guroot said:**
> You could try to create a new user and logon with it.

```
useradd -m user1
passwd user1
```
Jonathan
[http://www.guroot.com]("http://www.guroot.com?lang=en")

This is what I did, thank you very much.

Now I have to start all over again! :lol:

---

### Post by lidex on 2010-03-28
Not really. If you're on the system as another user just use nautilus to remove the "panel" folder in /.gconf/apps/ of your original user folder.

---

