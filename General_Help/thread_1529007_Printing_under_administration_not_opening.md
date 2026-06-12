---
title: "Printing under administration not opening"
date: 2010-07-11
forum: General Help
---

### Post by dmorlow on 2010-07-11
Hi,

I just noticed today that my Printing option under the ubuntu menu --> System --> Administration isn't working anymore.  I opened up the menu editor to see what the command it is when it works and it says it's the command...

system-config-printer

When running it at the command line, I get the message...

david@david-laptop:~$ system-config-printer
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 31, in <module>
    from timedops import *
  File "/usr/share/system-config-printer/timedops.py", line 20, in <module>
    import gobject
ImportError: No module named gobject


I'm focusing on the last part "No module named gobject."  I tried searching google for gobject to figure out where I get it from and no luck.  I can't think of anything recent I've changed in the config of my computer.

---

