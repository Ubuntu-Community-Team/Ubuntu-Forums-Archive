---
title: "Unclean shutdown after power failure"
date: 2009-10-07
forum: General Help
---

### Post by GeneLander on 2009-10-07
Hello everyone.  I had Ubuntu 9.04 running on an USB external hard drive connected to an Asus eeePC.  Worked great until we had a power failure for several hours.  Now when I start up the system and press ESC repeatedly to choose the USB drive, the Ubuntu startup line appears but at the bottom of the screen the message "unclean shutdown, checking drives" and a counter begins counting up what appears to be disk sectors.  When its done checking, a command line prompt appears and requests the root user password.  If I type it in, the result is a command line prompt instead of loading the Ubuntu GUI.  

Can anyone tell me how to restore the Ubuntu GUI?

-Gene

---

### Post by GeneLander on 2009-10-09
This was a long-standing problem and I've finally found a solution.  I tried several ways to view the contents of the USB external hard drive when attached to different computers (Mac, Windows) and it seemed to be OK.  I was almost ready to completely reformat the USB drive and reinstall Ubuntu when I found the following workaround.  When the maintenance shell says to enter password or  control-D that does not work.  Simply type "enter" and you will get to a command line prompt.  Then type fsck and the system will do a manual check of the USB hard drive.  Be patient and stay there to confirm (type "y") when it asks if you want to repair errors found.  Eventually, it will complete the repair process.  Then type command-D to restart the computer.  This worked for me.  Hopefully, it will work for you as well.

-Francis


> **GeneLander said:**
> Hello everyone.  I had Ubuntu 9.04 running on an USB external hard drive connected to an Asus eeePC.  Worked great until we had a power failure for several hours.  Now when I start up the system and press ESC repeatedly to choose the USB drive, the Ubuntu startup line appears but at the bottom of the screen the message "unclean shutdown, checking drives" and a counter begins counting up what appears to be disk sectors.  When its done checking, a command line prompt appears and requests the root user password.  If I type it in, the result is a command line prompt instead of loading the Ubuntu GUI.  

Can anyone tell me how to restore the Ubuntu GUI?

-Gene

---

