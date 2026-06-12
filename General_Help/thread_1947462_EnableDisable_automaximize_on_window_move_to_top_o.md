---
title: "Enable/Disable automaximize on window move to top of screen"
date: 2012-03-26
forum: General Help
---

### Post by Ralph L on 2012-03-26
Just installed oneiric and gnome-session-fallback.  Am using Gnome Classic.  I know there is a way to enable/disable automaximize of a window, when it is moved to the top of screen, but I can't find it on a web site.  I found one web site that says to use gconf-editor and go to :

- apps -> compiz-1 -> pluging -> grid -> screen0 -> options -> top_edge_action
set this value to 0.

However, it didn't work.  I don't know if Gnome Classic even uses Compiz.

Any help would be appreciated.

Ralph

---

### Post by soryu on 2012-03-26
if you have compiz  there is a setting in the window section or rules of ccsm where you can change that.
i'm on win7 right now so i cant see what it's actually called but it's there.

---

### Post by Ralph L on 2012-03-26
I found a web site that said that Gnome Classic uses compiz, and that Gnome Classic (no effects) does not.  I have started both of these  and under each have tried:
- apps -> compiz-1 -> pluging -> grid -> screen0 -> options -> top_edge_action
set this value to 0

It did not work.

Ralph

---

### Post by DesertF0x on 2012-05-15
you can try it via dconf-editor and turn off edge-tiling in org.gnome.shell.overrides but I am not quite shure if it works for gnome classic

---

### Post by Ralph L on 2012-05-23
Solved the problem by moving to Precise Pangolin.  Installed gconfig-editor with Synaptic and went to apps -> compiz-1 -> pluging -> grid -> screen0 -> options -> top_edge_action.  Set top_edge_action to 0.  Not sure whether or not I had to restart.

---

