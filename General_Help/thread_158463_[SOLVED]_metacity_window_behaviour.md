---
title: "[SOLVED] metacity window behaviour"
date: 2006-04-11
forum: General Help
---

### Post by gerases on 2006-04-11
I 've got a possibly simple question. I think one of the advantages of *nix window managers is that window behaviour can be so easily adjusted. 

What I would like to happen is this: when two windows are open and one is on top of the other, clicking on the window below SHOULD NOT minimize the window on top. This is the default behavour in fvwm I think. In KDE it was rather simple to set up as well. Well, I can't find anything for metacity and I wonder if it's possible at all.

If it's not, then I would like to switch to another window manager (sawfish?). I tried it yesterday by downloading sawfish, checking that it's the default alternative for x-window-manager but metacity kept starting up every time I restarted gnome. Is there a guide on how to change window managers in Ubuntu.

I don't really care about one window manager or another apart for that one feature.  It's what defines windows in *nix and I miss it a lot. 

Does anybody have any insight on this?

Any suggestions?

---

### Post by Monster_user on 2006-04-12
I was hoping that someone more knowledgeable than I would reply.

I know of three possible ways, but I haven't gotten the first to work. I don't know how to do the second. The third should work, in theory.

1. Install Gconf, the Gnome Configuration ("Registry") utility.
1a. Find the Entry that lists the Window Manager. Do a search for Metacity, and change it to a WM of your choice.

2. Create a file in your home folder, called **.gnomerc** That DOT is important. Then specify your window manager there.

You may just need to type the WM, and then include "--replace".

ratpoision --replace

3. Run the Session control panel, and then set the window manager to load at boot. Use one of the following commands, replacing kwin, with the WM of your choice.

kwin --replace
killall metacity && kwin

---

### Post by gerases on 2006-04-12
Very cool. I'm going to try it tomorrow and let you know how it went. Thanks for the reply!!!

---

### Post by IYY on 2006-04-12
No need to switch away from Metacity! I belive this feature exists:

Open gconf-editor (it's in the menu, but you can just type gconf-editor in the command line). Go to apps > metacity > general and unselect the field raise_on_click. 

Does that work?

---

### Post by gerases on 2006-04-12
Wow! It did work! I had to change to focus model from "click" to "mouse", but I can definitely live with that. Thanks a TON!

---

