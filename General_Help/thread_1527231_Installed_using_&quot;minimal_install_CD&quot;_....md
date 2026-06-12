---
title: "Installed using &quot;minimal install CD&quot; ... but where is &quot;open as root&quot; on right-click~?"
date: 2010-07-09
forum: General Help
---

### Post by bruceleejr on 2010-07-09
I installed Lucid Lynx 10.04 minimal install CD & installed XFCE.

But when I right-click something, there is no "open-as-root", I need this because I need to edit the "/etc/interfaces/network" file to set my static ip address.

How can I accomplish this~??


ps-= I previously had Linux Mint 9 Isadora installed, but there forums kept crashing for hours on end. I decided to install Ubuntu Lucid Lynx w/ XFCE & am very happy. =]

---

### Post by bruceleejr on 2010-07-09
bump

---

### Post by Spr0k3t on 2010-07-09
Alt-F2 -> "gksudo gedit /etc/interfaces/network"

That should get you covered for editing the file.  The open-as-root feature may be related to a nautilus addon or script you don't have installed.  Try the package nautilus-gksu to see if that does the trick.

Out of curiosity, why not use the network manager to set up your static IP address?

---

### Post by bruceleejr on 2010-07-09
Because I don't have network manager lol

I used Lucid Lynx minimal install CD. I installed XFCE4 and nothing came with it.

---

### Post by Spr0k3t on 2010-07-09
Wow, totally not awake here... missed the whole "minimal" and the "xfce" thing.  Not sure what you need to add for the thunar extension... totally different beast from nautilus.

---

### Post by bruceleejr on 2010-07-09
dangit, okay thanks

---

### Post by kerry_s on 2010-07-09
you can add it in your actions menu

name: open as root
command: gksudo exo-open %f

that should cover both folders & files, so you can check those box's.

---

### Post by bruceleejr on 2010-07-09
Holy crap, that is sick... thanks~!!! '


(havent tried it yet but this seems way more powerful than Windows XP)

---

### Post by nothingspecial on 2010-07-09
You could install wicd-curses which is an ncurses based terminal front end for wicd.

First thing I install after minimal.

---

