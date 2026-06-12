---
title: "USB Wireless Network Device problem"
date: 2010-07-03
forum: General Help
---

### Post by PabloTortilla on 2010-07-03
Hey guys,

Got a bit of a minor problem, and was wondering if there is a fix for it. For some reason, my USB wireless device isn't even recognised, unless I run "sudo modprobe ndiswrapper" every time I log on. After I do that, it works like a charm. So if there is no easy fix, I can live with it, but if there is, please tell, it gets annoying after a while :P

Thanks,
Pablo

---

### Post by PabloTortilla on 2010-07-04
Nothing?

---

### Post by PabloTortilla on 2010-07-08
Well, I solved my own problem. 

First off, I ran 
```
**sudo nano /etc/init.d/local.autostart**
```
to make a new file, which was editable in the terminal.

I then typed
```
*#!/bin/sh*
[I]sudo modprobe ndiswrapper
[/I]

```
and saved it (to save, have to exit it, and it will give you a Y/N option to save).

I then made it executable
```
**sudo chmod +x /etc/init.d/local.autostart**
```
and made it recognised as a startup script
```
**sudo update-rc.d local.autostart defaults 80**
```

Thanks go to this website >> [http://tips4linux.com/create-a-startup-script-for-debian-and-ubuntu-systems/](http://tips4linux.com/create-a-startup-script-for-debian-and-ubuntu-systems/)


Hope this helps people in my situation.

---

