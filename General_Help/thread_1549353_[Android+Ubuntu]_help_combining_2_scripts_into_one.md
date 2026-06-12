---
title: "[Android+Ubuntu] help combining 2 scripts into one"
date: 2010-08-09
forum: General Help
---

### Post by earthpigg on 2010-08-09
hi,

these two scripts are to tether an Ubuntu machine to an Android phone using the [easytether]("http://www.mobile-stream.com/easytether/android.html") app which allows the ubuntu machine to share the android device's internet connection over USB. (Why pay for the internet twice, if you only have one computer?)

The following two commands, according to the relevant documentation, must be run on the ubuntu machine in order to tether. I made them into two scripts for my sister and put them on her desktop.

I was wondering if anyone could help me combine them into one script. ideally, my sister would be able to double click on a *single* icon, enter her password, and be connected.

first script:
```
#!/bin/bash
gnome-terminal -x easytether connect [phone's serial number here]
```

second script:
```
#!/bin/bash
gnome-terminal -x sudo dhclient easytether0
```

the first one leaves text on the screen, and if you ctrl+c or close the terminal then the phone disconnects, so this must be left open. the documentation and onscreen message says that ctrl+c is the 'correct' way to un-tether the phone.

the second one needs to be run with sudo, and can be closed after it's done.

incidentally, i see no reason why we cannot submit this single script to the easytether folks to include in the .deb if we can figure it out.



if anyone wants to test this app for themselves, btw, the free version works the same - except it does not support https.

---

### Post by earthpigg on 2010-08-12
I got this response from the easytether folks when I emailed them:

> Our plan is to integrate EasyTether into Ubuntu connection manager.

In the interrum, anyone have any suggestions?

---

### Post by earthpigg on 2010-08-14
bump

---

