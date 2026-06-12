---
title: "Administrative tools fail to load"
date: 2010-05-09
forum: General Help
---

### Post by Yitzach on 2010-05-09
I found a similar problem. The poster used a similar title "Administrative tools fail to open - karmic"
I also have karmic and four tools fail to load; Ubuntu Software Center, Hardware Drivers, System Testing, and Update Manger. Synaptic and System Monitor run. I ran update-manager and software-manger and was told module pygtk does not exist. I ran "sudo apt-get install pygtk" and it said that did not exist as a package.
The terminal update and upgrade also work.

```
me@me-laptop:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 26, in <module>
    import pygtk
ImportError: No module named pygtk
me@me-laptop:~$ software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 25, in <module>
    import pygtk
ImportError: No module named pygtk
me@me-laptop:~$ sudo apt-get pygtk
[sudo] password for isaac: 
E: Invalid operation pygtk
me@me-laptop:~$ sudo apt-get install pygtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pygtk
me@me-laptop:~$ 

```Would the best solution be to reinstall the OS from fresh downloads as at least the Hardware Drivers tool works with the live USB?

---

### Post by Yitzach on 2010-05-09
pygtk is a member of python-gtk2. A simple reinstall worked.

---

