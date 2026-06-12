---
title: "Readonly &quot;desktop&quot;?"
date: 2011-04-01
forum: General Help
---

### Post by uqbar on 2011-04-01
Hi all.
I'm developing a customized Ubuntu installation in order to create a fool proof netbook to allow sales agents to just open it, stick a USB 3G modem and click on an icon to open an ssh connection to a central sales server.
I've trimmed down everything in the UI to be used: no icons other than the network manager applet and the battery level.
Everything is already working fine except that the users can still play by changing the task bar, delete the mentioned icon and so on.
I've already chown/chmod a few files but it's a very time consuming and error prone thing to be done.
For example, by doing:
# chown -R root:root ~agent/Desktop
# chmod -R 755 ~agent/Desktop
I can "secure" the launcher icons on the desktop.
What about the task bar?

TIA.

---

### Post by Azdour on 2011-04-01
Hi,

In the past I have used:

```
gconf-editor
```

Then looked through the options that I can set. Locking the panels can be done through:

```
gconftool-2 --type bool --set /apps/panel/global/locked_down true
```

There maybe other options in the gconf-editor that you want to play with.

---

