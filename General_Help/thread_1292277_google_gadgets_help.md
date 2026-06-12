---
title: "google gadgets help"
date: 2009-10-15
forum: General Help
---

### Post by windowsfree on 2009-10-15
I am experiencing problems getting them to run.  I have installed and uninstalled everything related to it, but cannot get them to start. I have installed through online at Google and also through the package manager.  
Any assistance will be greatly appreciated.

---

### Post by fooman on 2009-10-15
sorry,  do you mean they don't run at all? ...or you cannot get them to start when booting?

after installing,  look in applications > internet > google gadgets

or press the alt-f2 keys and when the run dialog box opens...type: ggl-gtk into the space and press "run"

if that does not work....try it in a terminal to see if any errors pop up.  open a terminal and type:

```
 ggl-gtk
```to get them to run at startup...try adding it to your "startup applications"

go to system > preferences > startup applications

when it opens,  click add...in the name space, type:
```
google gadgets
```in the command space, type or copy/paste: 
```
/usr/bin/ggl-gtk
```then log out and back in again to see if it works.

hope that helps.

---

### Post by windowsfree on 2009-10-16
Re-downloaded gadgets and now it works.......strange

---

