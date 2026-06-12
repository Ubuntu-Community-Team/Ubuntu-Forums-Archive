---
title: "Freeze at login"
date: 2006-03-22
forum: General Help
---

### Post by Natalie Erin on 2006-03-22
When I start up 5.10 it will load all of the way until it gets to a login screen, then it completely crashes.  I cannot hit CTRL+ALT+F1 to switch screens as that has locked up as well.  I presently do not have my gdm set to run at any point during a standard startup.  Also, when I restart in recovery mode, the only time that I can access the gdm is if I log in as root.  If I try to allow it to continue to a standard login, it freezes at that login.  I have tried reconfiguring my xserver-xorg and that has not helped (I have an ATI card).  When it does freeze, it is a complete kernel panic, as I cannot even get my num lock key to turn on at all.  Thanks for all of the help.

---

### Post by trent dillman on 2006-03-23
Try logging in at the text mode as root, then run a script like so:

```

#!/bin/bash
startx > xcrash.out 2>&1 &
sleep 60
killall X

```

maybe this will capture some output for the rest of us to look at.

(And if I got the syntax wrong, I apologise!)

---

