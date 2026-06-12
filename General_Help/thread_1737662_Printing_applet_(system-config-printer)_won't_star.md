---
title: "Printing applet (system-config-printer) won't start"
date: 2011-04-23
forum: General Help
---

### Post by leehach on 2011-04-23
Trying to add printers to a new install, and system-config-printer doesn't start. CUPS is working, and I am able to add and manage printers using [http://localhost:631](http://localhost:631), but I would prefer to use the applet.
```
lee@tycho:~$ system-config-printer
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 104, in <module>
    from GroupsPane import *
  File "/usr/share/system-config-printer/GroupsPane.py", line 21, in <module>
    from GroupsPaneModel import *
  File "/usr/share/system-config-printer/GroupsPaneModel.py", line 19, in <module>
    import libxml2
  File "/usr/lib/pymodules/python2.6/libxml2.py", line 1, in <module>
    import libxml2mod
ImportError: /usr/lib/pymodules/python2.6/libxml2mod.so: symbol xmlFirstElementChild, version LIBXML2_2.7.3 not defined in file libxml2.so.2 with link time reference
lee@tycho:~$ 

```
Libxml2 on my system is version 2.7.6. Python seems to be searching for version 2.7.3. I don't know if this is the problem, but how would I diagnose or fix?

Similar problems (possibly different causes) include [http://ubuntuforums.org/showthread.php?t=1717035]("http://ubuntuforums.org/showthread.php?t=1717035"), from only three weeks ago, but no responses, and this one [http://ubuntuforums.org/showthread.php?p=5784157]("http://ubuntuforums.org/showthread.php?p=5784157"), which I don't think is the issue because I don't seem to have an "extra" python install at /usr/local/bin/python.

Thanks, --Lee

---

### Post by Habeouscorpus on 2011-04-23
Try popping open Synaptic and see if it complains about broken packages or upgrades.

---

### Post by leehach on 2011-04-23
No broken packages or unmet dependencies (as far as apt is concerned). I also tried completely removing then reinstalling system-config-printer. That did nothing.

--Lee

---

### Post by leehach on 2011-04-25
Wow. This problem was ridiculous to run down, but it turns out it was the version of Postgres 8.4 I had on my machine, which apparently breaks libxml2.

First, Googling ```
ImportError: /usr/lib/pymodules/python2.6/libxml2mod.so: symbol xmlFirstElementChild, version LIBXML2_2.7.3 not defined in file libxml2.so.2 with link time reference
```
turned up [this thread]("http://ubuntuforums.org/showthread.php?t=1383483"), which pointed to [this Launchpad bug report]("https://answers.launchpad.net/ubuntu/+source/libxml2/+question/90804"), which basically said it's not system-config-printer, it's libxml2. But I tried complete removal / reinstall of python-libxml2, and that did nothing.

Then I found [this thread]("http://ubuntuforums.org/showthread.php?p=9615619"), which is about Evolution (!) not starting, but with the same error message I was getting trying to start the printer applet. Turns out it's Postgres 8.4, and specifically non-repository installers (I use EnterpriseDB). Rather than removing Postgres, I just had to use the StackBuilder to upgrade from 8.4.1.2 to 8.4.7.1, and now python can import libxml2mod, hence system-config-printer successfully launches.

---

