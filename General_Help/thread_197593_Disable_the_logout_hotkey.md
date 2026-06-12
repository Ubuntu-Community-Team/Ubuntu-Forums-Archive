---
title: "Disable the logout hotkey"
date: 2006-06-16
forum: General Help
---

### Post by Grog140 on 2006-06-16
I have lost so much data because of the logout hotkey. The key combo is <shift><Backspace> although I do not think this is standar.

I have it disabled under preferences and in key bindings. I have a feeling it is an XGL thing but I still can't find out where to disable it at. :confused: :confused:

---

### Post by BitTorrentBuddha on 2006-06-16
I'm running XGL/Compiz CVS and shift backspace doesn't do it for me, but I believe you're talking about the same thing as ctrl+alt+backspace, right? You restart X (also logging you out and bringing you to the login screen)? Any keybindings created by compiz should be able to be edited by running gconf-editor and navigating to apps -> compiz -> general then a combination between either "-> allscreens -> options" or "-> screen0 -> options".

---

### Post by Grog140 on 2006-06-16
Hmm, well I didn't set it to be like that.

And it is not in any of the XGl menus. So I guess I will have to dig further.

---

### Post by Ramses de Norre on 2006-06-16
There have already been a lot of threads about this issue, do a search and I'm sure you'll find the answer.

---

