---
title: "hang at shutdown"
date: 2010-05-02
forum: General Help
---

### Post by brotherz on 2010-05-02
Hello.  I am a somewhat new user.  Ever since a recent update, which included a kernel update, my system shuts down at the shutdown command but the power does not go off.  Sometimes I can see a call trace but at other times the screen is just dark.  In either case, there is no response to the keyboard.  After powering off and starting up again, I have tried looking in various logs to see if events at shutdown have been captured somewhere, but I haven't discovered where the record might be. 
   I wonder if this is a bug.  Would appreciate any guidance. 
   My system: version 9.10, kernel 2.6.31-21-generic.  Mem 1001.8 MiB. 2x Pentium 4 CPU 3.20 GHz. video ATI Radeon R350.  40G SATA hd with 28G free.

---

### Post by jrushslo on 2010-05-06
I found usable this workaround:
I go to /boot/ directory, create "old" directory and then move all  *2.6.31-21* files to this directory. Before this you must have also  another version of kernel installed (for example i have 2.6.31-20).
After moving files i update grub.cfg automatically with command  "update-grub".
After next reboot you will have another kernel active.
You can check it before and after changes with command "uname -r".
Good luck!

---

