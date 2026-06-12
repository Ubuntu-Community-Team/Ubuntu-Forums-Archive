---
title: "Gnome Activity Journal startup errors"
date: 2011-05-13
forum: General Help
---

### Post by micah1104 on 2011-05-13
Hello there ^_^

Whenever I try opening the Gnome Activity Journal from Applications > Accessories > Gnome Activity Journal, it doesn't open, nothing shows up, and not even in the System Monitor.  So I took a different route, by opening it from the Terminal, to see if it gave me anything, and when I type in 'gnome-activity-journal' it spits this out at me:

```
micah@micah-N120:~$ gnome-activity-journal
Traceback (most recent call last):
  File "/usr/bin/gnome-activity-journal", line 94, in <module>
    from src.main import PortalWindow
  File "/usr/share/gnome-activity-journal/src/main.py", line 30, in <module>
    from activity_widgets import MultiViewContainer, TimelineViewContainer, ThumbViewContainer
  File "/usr/share/gnome-activity-journal/src/activity_widgets.py", line 35, in <module>
    from store import ContentStruct, CLIENT
  File "/usr/share/gnome-activity-journal/src/store.py", line 504, in <module>
    STORE = Store()
  File "/usr/share/gnome-activity-journal/src/store.py", line 367, in __init__
    days_population = ZeitgeistDBusInterface().get_extension("Log", "journal/activity").GetHistogramData()
  File "/usr/local/lib/python2.7/dist-packages/zeitgeist/client.py", line 108, in __getattr__
    raise TypeError("Unknown method name: %s" % name)
TypeError: Unknown method name: GetHistogramData

``` 

Anyone else have this error or had and fixed it?

Thanks in advance :)
~Micah1104

---

### Post by _graham_ on 2011-08-21
I had the same problem in 11.04. I think it was after I did an update to zeitgeist and it failed to restart properly. After restarting the zeitgeist services the Activity Journal worked. I found the answer here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-activity-journal/+bug/638359](https://bugs.launchpad.net/ubuntu/+source/gnome-activity-journal/+bug/638359)

---

