---
title: "How to reinstall Terminal?"
date: 2011-06-25
forum: General Help
---

### Post by polardude1983 on 2011-06-25
I had recently re-installed Ubuntu and had it point to my old /home dir. Anyways whenever I load up terminal just the cursor shows no christoph@christoph-desktop: whatever just a blank cursor.

I can type but nothing would happen it would be like typing into a text editor.

Then suddenly it severely bogs down my system and my screen get darker and then the terminal eventually kills itself and goes away.

Any help lol.

---

### Post by el_koraco on 2011-06-25
You always have access to six virtual consoles. You hit CRTL + ALT + F1 (all the way to F6). You login, and then do 

```
sudo apt-get install --reinstall gnome-terminal
```

or you can open Synaptic, find the gnome-terminal package and mark it for reinstall. You get back to the GUI with CTrl ALT F7

---

### Post by polardude1983 on 2011-06-25
I tried through synaptic and did a reinstall of gnome-terminal and data. Though it did not solve my problem. I must of had some script that altered the gnome-terminal in some way before my reinstallation of the OS. After the OS install it must still be looking for that.

---

### Post by polardude1983 on 2011-07-13
Still having the same problem. even after reinstalling gnome-terminal

---

