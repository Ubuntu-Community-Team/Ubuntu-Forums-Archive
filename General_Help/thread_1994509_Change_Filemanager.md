---
title: "Change Filemanager"
date: 2012-06-02
forum: General Help
---

### Post by ausnacht on 2012-06-02
I would like to change my filemanager from pcmanfm to nautilus. I've installed nautilus. 

First I tried to right click filemanager under accessries ->filemanager however when I change the command and click ok it resets it back to pcmanfm. I tried logging off and back on. I tried searching for nautilus graphically. 

I searched google and tried several things. One suggestion was to change the pcmanfm file but I couldn't find it with either find or locate. 

I tried searching the forms

The only thing I haven't tried is writing a script. Any ideas? This is while I left lubuntu for a while. We use linux so we can use it however we want.

---

### Post by LiamOS on 2012-06-02
To what extent do you want Nautilus to be the default?

I've been having an issue or two along the same lines, and as far as I can tell, the lubuntu-desktop, lubuntu-core, etc. packages depend on PCManFM to be installed. Whether they actually need it, or merely have it as an unnecessary requirement, I don't know. If you're not adverse to editing source and recompiling, this might be worth a look, but is probably more bother than it's worth.


Edit: Tested the solution idea I had here; didn't work.

Edit2: If you want to disable pcmanfm's controlling your desktop, removing the [Desktop] lines from ~/.config/pcmanfm/Lubuntu/desktop.conf seems to do the trick. That location is off the top of my head, so it might be slightly different, but it should be easy to find.

---

