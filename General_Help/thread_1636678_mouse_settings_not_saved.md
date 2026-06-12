---
title: "mouse settings not saved?"
date: 2010-12-03
forum: General Help
---

### Post by CIement on 2010-12-03
So I am trying to use the "syndaemon -i 1 -t -k -d" settings, and they work fine, except that I have to type it in every time I turn on the computer. I tried putting it into the

System/Preferences/Startup Application 

thing in the GUI, but it doesn't seem to be working, because when I type I can still click, but if I type it into the terminal it doesn't exhibit the same behavior anymore.

Also, I wanted to use 

synclient RTCornerButton=0 and synclient RBCornerButton=0 

but I have no idea how to save those settings. I read online somewhere that you are supposed to edit your 

/etc/X11/xorg.conf.d/10-synaptics.conf

file, but the xorg.conf.d folder didn't even exist for me, as did that file, so I just made them and added some lines, but that also doesn't seem to work. I can't seem to find any documentation on how to edit X11 at all, so any help would be greatly appreciated. It'd be nice if you could explain how all this works to me, as I'm fairly new to using Linux but I'm more than willing to learn.

---

