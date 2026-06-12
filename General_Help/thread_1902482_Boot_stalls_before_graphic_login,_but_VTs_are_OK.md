---
title: "Boot stalls before graphic login, but VTs are OK"
date: 2011-12-30
forum: General Help
---

### Post by linfidel on 2011-12-30
I upgraded to 11.10 recently, and everything was good.  I wanted to take a look at Gnome3, so I installed that, although I had some problems with the gnome UI's text display on startup, it went away after resizing fonts larger and back to normal.

I played around a little with the tweak app, then shut down.  Now, it won't boot to the login prompt.  It stalls on some test (screen says it's checking the state of the battery or something similar, but this is not a laptop).

I can get to the virtual terminals and log in, or I can do ctrl-alt-del and it will restart.

Any suggestions on where to go from here?  I installed fresh into another partition, but it would be nice to fix it instead of spending so much time reconfiguring, especially since I plan to get a new drive soon and reinstall then.

Thanks to anyone who can help.

---

### Post by 2F4U on 2011-12-31
If you can get to a virtual terminal then you will be able to look into the system log files. Here are some interesting ones that may contain more info on where it hangs:
- /var/log/dmesg
- /var/log/Xorg.0.log
- /var/log/syslog
- .xsession-errors in your home folder

---

### Post by linfidel on 2011-12-31
> **2F4U said:**
> If you can get to a virtual terminal then you will be able to look into the system log files. Here are some interesting ones that may contain more info on where it hangs:
- /var/log/dmesg
- /var/log/Xorg.0.log
- /var/log/syslog
- .xsession-errors in your home folder
Thanks for the help.  I did look at dmesg, but didn't see anything I could figure out as being useful - it's hard, because I think a lot of errors are expected, but still listed, so it's hard to know which ones matter.

I think what would be really useful would be to find a good tutorial or documentation on exactly what the boot sequence is.  I know it's something right before the login prompt - what used to be GDB, but I guess it's LightDM now.  It might even be that, itself, not running for some reason.  I guess it might use X by this time - do you by any chance know?  I was assuming that, since it doesn't yet know who is logging in, that it wouldn't be anything in my home folder at all.  Anyone know if this is the case?

I've got systems on other partitions, and I installed a clean version on another one, then copied a lot of whole directories from the working partition to the old one, but not my home directory.  None of it made any real difference, so far.

---

### Post by linfidel on 2012-01-29
BTW, this happened again after playing around with Gnome 3 shell.  This time, though, I managed to recover by replacing my xorg.conf file from a working backup.

Needless to say, I've abandoned Gnome 3 shell for good.  I've somewhat abandoned Unity, too, for the Gnome classic mode with Compiz, which works well for me after discovering the magic key-mouse combination to enable right-clicking on the panel (meta-Alt-rightclick).

Now I'm playing around with alternate launchers like AWN, Cairo dock, etc.

---

