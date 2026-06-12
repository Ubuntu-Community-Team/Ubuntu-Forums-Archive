---
title: "Notebook Display on/off with shortcut"
date: 2010-07-22
forum: General Help
---

### Post by nike234 on 2010-07-22
Hi!
Here's what I did:
Used the Compiz-Manager and Commands to add the commandline: "xset dpms force off".
Assigned the shortcut: ctrl-alt-k to it.

This is supposed to shutdown the screen. It does, but the screen turns back on right away.

My Questions:
1) Is there a different command, that will shutdown the screen permanently (until I move the cursor?).
2) Are there commands to lower/raise the brightness of the screen (my default key-shortcut is: "Fn-Left-Arrow"//"Fn-Right-Arrow")

My System:
Acer Aspire 1410
2 GB Ram
Dual-Core @ 1.2 Ghz
Running Ubuntu 10.04 64bit

Thank you for any help :)
-nike234

---

### Post by simptechmike on 2010-07-22
Add in a 1 second delay to the beginning and it should work:

*sleep 1; xset dpms force off*

Source: [http://www.shallowsky.com/linux/x-screen-blanking.html](http://www.shallowsky.com/linux/x-screen-blanking.html)

---

