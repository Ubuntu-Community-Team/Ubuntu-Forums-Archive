---
title: "Cannot open &quot;Printing&quot;"
date: 2010-12-23
forum: General Help
---

### Post by appster on 2010-12-23
When I go to System->Administration->Printing no window pops up. Down on the bottom panel it says "Starting Printing" and then goes away. I'm trying to install my HP Deskjet printer, and any help is much appreciated!

--Appster

---

### Post by slooow on 2010-12-23
# do a google search for <your printer brand & model>, cups, (linux)
# if you are confident that the printer is supported, type
localhost:631 into your browser
# you can configure it from there if cups is installed

---

### Post by AlphaLexman on 2010-12-23
...Or from a terminal enter:
```
system-config-printer --debug &
```
...and post the output.

**Note:** the ampersand (&) will force the program to run in the background!

---

### Post by appster on 2010-12-24
> **AlphaLexman said:**
> ...Or from a terminal enter:
```
system-config-printer --debug &
```...and post the output.

**Note:** the ampersand (&) will force the program to run in the background!

Here's the output:

```
system-config-printer --debug &
[1] 1752
edward@edward-desktop:~$ Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 31, in <module>
    from timedops import *
  File "/usr/share/system-config-printer/timedops.py", line 20, in <module>
    import gobject
ImportError: No module named gobject
```

---

### Post by blitzit on 2011-10-11
Same problem here. And don't seem to be able to solve it. I re-installed cups but that didn't help either.

---

