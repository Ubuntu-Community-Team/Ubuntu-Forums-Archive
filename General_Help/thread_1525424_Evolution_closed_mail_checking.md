---
title: "Evolution closed mail checking"
date: 2010-07-06
forum: General Help
---

### Post by w4rh4wk on 2010-07-06
hello there,

there are a few posts around asking how to put evolution into tray. i dealt with that, but i got a much more interesting point of view for this "problem".

Ubuntu 10.04 has the new indicator applet for the gnome panel. in it there is this very handy mail indicator working as launcher for empathy, evolution and pidgin (if installed), holds your currently opened conversations and shows when a new mail arrives.

but this mail checking is only done when evolution is opened.
now my question: is there a way to minimize evolution to the indicator mail applet? i don't want to have a new tray icon, the mail indicator icon works fine. i want evolution to stay away from my taskbar but still checking for my mails.

---

### Post by doko1 on 2010-07-09
Same here. 

What is the indicator applet good for, if Evolution does not check for new mails in the background? 

Is there a solution to this? 

Because I want exactly the same thing: 
I want Evolution to stay away from my taskbar but still checking for new mails.

---

### Post by timgood on 2010-07-09
```
sudo apt-get install mail-notification
```

Hope this helps.

---

### Post by w4rh4wk on 2010-07-09
> **timgood said:**
> ```
sudo apt-get install mail-notification
```

Hope this helps.

i don't wanna use mail-notification or any other applet like that one. not because i don't like them, but because the mail-indicator should already do this. + if i get notified about new mails, the mail-indicator should do that, not another program.

---

### Post by philinux on 2010-07-09
> **w4rh4wk said:**
> i don't wanna use mail-notification or any other applet like that one. not because i don't like them, but because the mail-indicator should already do this. + if i get notified about new mails, the mail-indicator should do that, not another program.

Move Evolution to Desktop 4. ;)

---

### Post by w4rh4wk on 2010-07-09
> **philinux said:**
> Move Evolution to Desktop 4. ;)

that's the way i have it now. just wanna have an improved mail-indicator.

---

### Post by philinux on 2010-07-09
> **w4rh4wk said:**
> that's the way i have it now. just wanna have an improved mail-indicator.

Yes it's a bit of a pain. I'm just resigned to having it open.

[edit] just found this. But readme is empty.
[http://gnome.eu.org/evo/index.php/Evolution_Tray](http://gnome.eu.org/evo/index.php/Evolution_Tray)

More here.
[https://bugs.launchpad.net/ayatana-ubuntu/+bug/460483](https://bugs.launchpad.net/ayatana-ubuntu/+bug/460483)

---

