---
title: "Sound or Network Icon Missing from Indicator Applet"
date: 2011-02-10
forum: General Help
---

### Post by Githlar on 2011-02-10
I have an annoying problem. It started with the network icon in the indicator applet in gnome-panel. It just disappeared! Somehow I managed to get my network icon back (perhaps after a restart), but as soon as it showed up, my sound icon disappeared.

I followed some advice I saw somewhere that said to add another indicator applet. When I did I had my network icon on my pre-existing indicator applet and a sound indicator in the new one, but no network icon. Because I needed the sound icon, I closed the original.

But, I'm still stuck with no network icon now. This is pretty frustrating.

---

### Post by Githlar on 2011-02-11
Nobody?

---

### Post by Frogs Hair on 2011-02-11
Try to Reset panels to default using.```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by Githlar on 2011-02-12
What do you know? It worked! --recursive-unset looks like a nifty option! I didn't even think about looking in gconf, stupid me.

---

