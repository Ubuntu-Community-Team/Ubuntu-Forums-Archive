---
title: "Keyboard shortcuts dont work! Ubuntu 10.4"
date: 2010-06-02
forum: General Help
---

### Post by hydrox24 on 2010-06-02
I have just upgraded from karmic to lucid (9.10-10.4) and many keyboard short-cuts seem to be malfunctioning, most notably things used in word processing like ctrl-z, ctrl-v,ctrl-x and so on. I have already looked around for a solution but the only one I could find was to install glipper, which I have and it doesn't fix the problem. When I hit ctrl-c to copy however it turns up on the glipper clipboard but I cant paste it using shortcuts (right clicking and pasting works though).
Any help would be greatly appreciated.

(also this is my first post so tell me anything I might have done wrong)

---

### Post by arrange on 2010-06-02
First check the keys: go to *System &#8594; Preferences &#8594; Keyboard Shortcuts*, choose a line with a *disabled* shortcut, click on it, and check if different key combinations appear (f.e. if you press Ctrl+x, the line should read Ctrl+x; remove via *Backspace*).

Also provide the output of the command```
dpkg -l | grep xkb
```

---

### Post by hydrox24 on 2010-06-03
I have tried your suggestion however all the shortcuts that say "disabled" do not have key combinations assigned to them, I feel like tis may stop me from using ubuntu as It is quite a significant setback for me.:(

---

### Post by hydrox24 on 2010-06-11
solved the issue by turning off a compizconfig settings manager (ccsm) short-cut that was using the ctrl key, specifically for toggling the fire effect
thank-you for the help! now I am back to using Ubuntu whenever I can!

---

