---
title: "getting two finger middle click back"
date: 2009-11-09
forum: General Help
---

### Post by Vyrlokar on 2009-11-09
9.04 allowed me to perform middle click with a two finger tap on the touchpad and right click with a 3 finger one, but I find I usually need middle click (to open things in tabs, for example) and you can always use the hardware button for right click. Is there a way to revert to the 9.04 setting

---

### Post by wersdaluv on 2009-11-09
I want too!

---

### Post by osttov on 2009-11-18
Hello, I found the following answer [HERE]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/432814"), and it worked for me...

If you need a workaround until the fix (?), this one has been pointed out on the forums:

  synclient TapButton2=2; synclient TapButton3=3;

However, those commands have to be run at each session's start (you can add them in Preferences &#8594; "Startup Applications").

---

