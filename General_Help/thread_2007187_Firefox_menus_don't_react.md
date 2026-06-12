---
title: "Firefox menus don't react"
date: 2012-06-20
forum: General Help
---

### Post by QueenKwong on 2012-06-20
Hi,
I have a funny but somewhat annoying problem since I installed updates few days ago.
My OS is ubuntu lucid, netbook remix on an Asus EeePC.

In Firefox, the menues and anything else that pulls down, the items in search bar for example, do no longer react to clicking on them. So I am unable to use any menu item, no bookmarks, and the list of recent pages that normally appear when typing in the adress line either.
I cannot enter into the menu bar with F10 either, I don't even know how to bring up the Properties window.

I have tried reinstalling Mozilla Firefox from the repositories. No success
I have moved my profile folder and created a new profile. That seemed to fix ithe issue at first, but next day it was back again!

When I start firefox from a command line with 'firefox -P' and choose a profile - any profile - it seems to be working fine.
But from the desktop icon in the netbook launcher, the menues play dead again.

Has anybody experienced anything similar and knows what to do?
Where do I find out what the netbook launcher icons do exactly, and maybe try something there?
Any other ideas?

Thanks in advance, QK

---

### Post by QueenKwong on 2012-06-22
[INDENT]I still have no idea what caused the bug, but here's how I fixed it:
[/INDENT] 
I removed the Firefox icon from favorites.

At the login screen, I chose the normal Gnome desktop instead of the netbook launcher. (I possibly could have omitted this)

I started Alacarte, the Gnome-menu-customization tool. (Turns out this one also works for the netbook launcher, i should have figured this out earlier.)

I created a new menu item, an application launcher to start "/usr/bin/firefox". This is what worked from the shell.

Back on the netbook desktop, I put the new icon back into my favorites.

No problems so far.

---

### Post by snisson on 2013-01-03
This solution worked for me too.

Few days ago I installed EasyPeasy Linux on my PackardBell Netbook and had the same problems with Firefox. Menu wasn't working at all and right click didn't work too.

I tried several solutuons, but without result.

Finally I created new shortcut in Alacarte (System/Preferences/Main menu) which invites /usr/bin/firefox

Now it works great. Thanks.

---

