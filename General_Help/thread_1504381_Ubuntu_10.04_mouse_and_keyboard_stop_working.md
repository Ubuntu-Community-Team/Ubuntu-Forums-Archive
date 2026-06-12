---
title: "Ubuntu 10.04 mouse and keyboard stop working"
date: 2010-06-07
forum: General Help
---

### Post by brian023 on 2010-06-07
I was having a problem with the mouse and keyboard randomly failing to work after upgrading to version 10.04. I tried both the 32 and 64 bit versions. The problem went away after I edited the file /etc/default/grub and changed the following line:
from
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic nolapic"

If you are unable to open a terminal window, try doing the following
Ctrl+Alt+F1
Log into you account.
sudo nano /etc/default/grub
After saving your changes and exiting nano you can reboot by using the halt command.
(FYI Ctrl+Alt+F7 gets you back into X server -- but you need to reboot for the change to take effect)

**Update: problem recurred.**
I had to do Ctrl+Alt+F1 to log into a console.
I executed 'ps aux | more' to find the PID for X.
Using the PID I restart X with 'sudo kill -S SIGTERM <PID>'.
Once it started up again it was fine.

I'm still searching for a solution.

---

### Post by bdufflebag on 2010-09-10
Mmmkay. Now can you read this thread and help me out... please.  

[http://ubuntuforums.org/showthread.php?t=1572326](http://ubuntuforums.org/showthread.php?t=1572326)

---

