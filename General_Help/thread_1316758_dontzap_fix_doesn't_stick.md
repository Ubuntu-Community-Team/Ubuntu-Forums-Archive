---
title: "dontzap fix doesn't stick"
date: 2009-11-06
forum: General Help
---

### Post by crimius on 2009-11-06
I have been applying the dontzap workaround (keyboard>layout>layout options) and it works great.  my only issue is that the setting does not want to stay set between boots.  between sessions it works fine, just every time i restart my computer I have to go back and re-enable it.  Is there a reason for this or am I alone in encountering this issue?

---

### Post by t0p on 2009-11-06
If Karmic is the same as Jaunty: you can install the program called **dontzap**

```
sudo apt-get install dontzap
```then run it like so:

```
dontzap --disable
```

There's also info [in this thread]("http://ubuntuforums.org/showthread.php?t=1178967") on editing your xorg.conf to do the same.

---

### Post by crimius on 2009-11-06
do the xorg fix and the keyboard layout conflict with each other?  I had my xorg set to do the same in 9.04 (since installing a sperate program to access already built in functionality seemed a bit foolish).

I am using the same xorg files from my previous installation, yet every time i boot my laptop and switch .conf files to use an external display, ctrl+alt+bkspc is busted and I have to use the layout workaround to re-enable it.  when switching back to use my laptop display, however, this is not an issue.

---

