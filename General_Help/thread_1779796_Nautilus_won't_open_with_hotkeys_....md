---
title: "Nautilus won't open with hotkeys ..."
date: 2011-06-11
forum: General Help
---

### Post by Bucky Ball on 2011-06-11
Hi all,

Strange one. I'm using Gnome on 10.10 and use hotkeys (shortcut keys) for opening just about everything. When I go to System>Administration>Preferences>Keyboard Shortcuts and enter a shortcut to open Nautilus (file manager) it doesn't work. 

The shortcut key I have set for this (Mod4-m or Windows key+m) works fine if I replace 'nautilus' with 'thunar' or 'pcmanfm' as the command, but when I use 'nautilus', nothing. The same shortcut key works fine to open Nautilus in Xfce. If I type 'nautilus' in a terminal in Gnome up she pops. 

Any ideas why this is happening? I can stick just about any other command in there and WinKey+M will work fine. :-k

My regular setup is with Xfce where everything is dandy but I am fairly curious as to what Gnome has against Nautilus in the shortcut key menu.

---

### Post by Bucky Ball on 2011-06-12
Anyone?

---

### Post by hakermania on 2011-06-12
Your purpose is to solve the problem why is this  happening or to make it work?
If the later, then you can install compiz and use its shortcuts (it's called 'Commands')

---

### Post by mc4man on 2011-06-12
assuming gnome-classic login it works fine here
There is an existing one under Desktop > Home, the default for that here is Alt+Home.
So you could edit that one's binding or create a new custom one. For a new custom (super+m) just try full path in command
nautilus /home/<username>
or
nautilus --no-desktop /home/<username>

---

