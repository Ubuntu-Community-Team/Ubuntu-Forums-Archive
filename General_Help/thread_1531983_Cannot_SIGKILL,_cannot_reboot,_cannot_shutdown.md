---
title: "Cannot SIGKILL, cannot reboot, cannot shutdown"
date: 2010-07-15
forum: General Help
---

### Post by Bystroi on 2010-07-15
I have a remote server (Xubuntu 10.04) which suffered an electricity brownout yesterday. The server itself is backed with an ups, but it is connected to a external firewire disk, which is not, and this disk malfunctioned as a result of the brownout.

The problem:

Now, any process trying to access the external disk freezes and ends up in eternal D state in the process list, including ls and umount. Even trying to ls a directory which contains a symbolic link to a file in that drive just causes ls to freeze.

These processes cannot be killed even with SIGKILL, so I proceeded to reboot but...

None of the reboot commands work. Instead they just get added to the ever increasing list of D state processes. I tried (sudo) shutdown -r now, reboot -f now and finally plain shutdown -h now.

Is there anything else to try other than ask somebody to actually go to the server and pull the plug (which is not at all trivial)? Some way to tell kernel not to worry about messing stuff up, and just reboot?

---

### Post by Bystroi on 2010-07-19
I got the disk unplugged, which allowed the server to reboot. After that everything works fine again.

I guess there is simply no way to work around such situation. Unload kernel module or smtg, so I'm marking this now as solved.

---

