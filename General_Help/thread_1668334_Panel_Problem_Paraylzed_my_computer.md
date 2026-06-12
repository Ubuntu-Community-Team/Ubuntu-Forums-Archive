---
title: "Panel Problem: Paraylzed my computer"
date: 2011-01-16
forum: General Help
---

### Post by strange_cathect on 2011-01-16
I wanted to create another panel on my computer. I created one, which formed directly above one that I already had (at the bottom of one of my two screens). Just out of curiosity I asked it to autohide. That was a big mistake.

Now, I am unable to right click to remove or change the panel (the right click menu doesn't appear). This is true for all my panels. I thought logging out might fix it. No luck. Restart. No luck. Now my "top level" panel won't load, which means I don't have access to any of the main menus at all.

Basically, the only think I can access at this point is what is on my desktop.

Is there some way to fix this? Help!

---

### Post by strange_cathect on 2011-01-16
Got it. If anyone has this problem, I solved it this way:
> 
1. Created a launcher for terminal: Right click on desktop, select create launcher, command is: /usr/bin/gnome-terminal

2. Opened Nautilus from terminal with command: nautilus.

3. Navigated to: .gconf/apps/panel/toplevels in the /home directory.

4. Deleted the last panel folder; in my case: panel_3

5. After delete, my other panels appeared and were then able to be edited as normal.

I'll submit this as a bug...

---

