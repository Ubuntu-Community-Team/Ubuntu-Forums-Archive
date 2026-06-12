---
title: "Ctrl+Alt+Backspace fails to restart X.  However, X starts fine on reboot. Why?"
date: 2006-05-15
forum: General Help
---

### Post by KillrBuckeye on 2006-05-15
I made changes to my xorg.conf file so that the side buttons on my mouse (MS Intellimouse optical USB) would be recognized.  I simply made the following changes to the mouse section of the file (found in another thread):

- Changed "Protocol" from "ImPS/2" to "ExplorerPS/2"
- Added the option "Buttons" "7"

These changes actually work--the side buttons are now functional.  However, now I have noticed that Ctrl+Alt+Backspace just brings me to a command prompt (X doesn't restart).  It definitely worked before making this change.  The odd thing is that if I reboot my system, everything seems perfectly normal.  I am relatively new to Linux, so I have no idea what would be causing this type of behavior.  Any ideas?

---

### Post by imaiden22 on 2006-10-22
i can relate to this problem and just thought i'd bump this one up rather than make a new thread. the only difference is that my problem is restarting x gives me the gui login but upon entering my information the desktop fails to load and it freezes, but on a normal reboot it loads up fine and without a hitch. can anyone give their thoughts on why this is?

---

### Post by hmm on 2006-11-03
I have a same problem. Please help me :)

---

### Post by puppy on 2006-11-03
yep same here - logout, restart etc have full functionality but ctrl-alt-backspace just gives me a black screen with a flashing cursor in the top left, but... nothing happens - it just sits there - I've even gone away and made a cup of coffee and it's still unchanged when I get back. I have to do a hard restart... 

This has only been happening fairly recently also - anyone got a fix?

---

