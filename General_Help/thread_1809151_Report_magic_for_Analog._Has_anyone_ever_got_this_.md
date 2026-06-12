---
title: "Report magic for Analog. Has anyone ever got this working on Ubuntu?"
date: 2011-07-21
forum: General Help
---

### Post by ingramproductions on 2011-07-21
I'm just curious if anyone has ever got Report Magic for Analog working on Ubuntu. The package name is rmagic. There is hardly any good documentation for it. The only real info I could find on it is from their documentation section:
[http://www.reportmagic.org/docs/overview.html]("http://www.reportmagic.org/docs/overview.html")
If I run rmagic that was installed from the repositories, this is what I get:
```
root@webserver2:/etc/rmagic# rmagic
Report Magic 2.21
Copyright (C) 1999-2003 Wadsack-Allen. All rights reserved.
rmagic: WARNING: The setting "[graphs] Reverse_Time" is not recognized. It will be ignored.
gd warning: one parameter to a memory allocation multiplication is negative or zero, failing operation gracefully
Can't call method "can" on an undefined value at /usr/share/rmagic/wadg/rm/Settings.pm line 918.

```
I couldn't get that to work, so I installed from the source package and this is what I get:
```
root@webserver2:/usr/local/bin/rmagic-2.21# ./rmagic.pl 
gd warning: one parameter to a memory allocation multiplication is negative or zero, failing operation gracefully
Can't call method "can" on an undefined value at /usr/local/bin/rmagic-2.21/wadg/rm/Settings.pm line 928.
```
BTW, Analog is working just fine. I've got Analog to export it's reports to the correct web directory to confirm it works. Then I changed it to COMPUTER output and it exported a dat file for Report Magic.
Attached are my 2 rmagic.ini files, one of them from the repository install, and the other from the source install.
Any help would be greatly appreciated!

[ATTACH]197967[/ATTACH]

[ATTACH]197968[/ATTACH]

---

### Post by ingramproductions on 2011-07-22
Apparently there is a bug that was reported in January of 2009 and still hasn't made it's way into the latest release.

[https://bugs.launchpad.net/ubuntu/+source/rmagic/+bug/315280]("https://bugs.launchpad.net/ubuntu/+source/rmagic/+bug/315280")

 I think this is because there haven't been any more releases. All the dates on there website  are extremely old, their mailing lists are a joke, and the support email domain doesn't even exist anymore (dgsupport@wadsack-allen.com)! Anybody considering using this, take that into consideration.
On the other hand, the patch works and Analog/Report Magic still do a very good job.

---

