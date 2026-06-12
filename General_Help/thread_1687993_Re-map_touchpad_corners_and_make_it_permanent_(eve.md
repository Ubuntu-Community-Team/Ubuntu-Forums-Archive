---
title: "Re-map touchpad corners and make it permanent (even after system restart)"
date: 2011-02-14
forum: General Help
---

### Post by blehmeco on 2011-02-14
Ok guys, just can't find the answer for this one (after Google and these forums)...

So I want to configure my Synaptics touchpad in this fashion:

```
synclient RTCornerButton=8 RBCornerButton=10 LTCornerButton=11 LBCornerButton=12 FastTaps=1
```This line of code does what it's intended of it. However, the changes made don't really stick after a system reboot...I'll explain:

So, the "FastTaps" part works flawlessly (as intended).
However, the corners bit doesn't work after system reboot!...and weird enough, if I set up a start up script with that bit of code on it it'll only remap the last two corners (LT and LB), because RT and RB always get automatically set to "2" and "3"...
It's obvious then that those corners are getting remaped somewhere I haven't found yet...

I've already tried [**ppa:yurivkhan/ppa**]("https://launchpad.net/%7Eyurivkhan/+archive/ppa") and adding new options to "usr/lib/X11/xorg.conf.d/10-synaptics.conf" to no avail either...

Any ideas how to make the remap of touchpad corners permanent?


P.S. - I'm using Ubuntu 10.04 LTS with Macbuntu.

---

### Post by tudor117 on 2011-02-14
Have you tried making a script with that command and adding it to System&#8594;Preferences&#8594;Startup Applications?

---

### Post by blehmeco on 2011-02-15
Ooops!...sorry! Just noticed I didn't mention that!
 
Yes, when I said it didn't work completely after reboot (only some of the re-mapping worked) that was with a script added to the start up applications!...among other stuff that script included that line of code on first post!

---

### Post by blehmeco on 2011-02-15
So in the meantime after a few more digging I eventually stumbled across [a working solution]("http://ubuntuforums.org/showpost.php?p=9634220&postcount=4")!

I just changed the folder of the files (yes, in the code too) and the "synclient" line and now every corner of the touchpad and "FastTaps" get correctly configured even after reboot!

Hope this helps anyone with the same problem

Cheers!


EDIT:

Admitedly, since the working solution posted above implies a constant loop, and it's not that pretty, I've managed to find  a second and maybe simpler way to solve this problem...
It's pretty basic, but somehow I didn't remember it at first (don't ask me how)...
I just put this code (among other stuff) in a script on startup applications:

```
sleep 5
synclient RTCornerButton=8 RBCornerButton=10 LTCornerButton=11 LBCornerButton=12 FastTaps=1
```(you know, just in case this could be helpful for anyone else...)

---

