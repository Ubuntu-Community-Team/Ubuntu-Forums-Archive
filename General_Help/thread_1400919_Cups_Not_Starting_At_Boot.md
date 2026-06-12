---
title: "Cups Not Starting At Boot"
date: 2010-02-07
forum: General Help
---

### Post by klausner on 2010-02-07
I can't get cups to auto-start at boot time. Running *sudo cupsd* manually works fine, but I don't want to have to do that every session.

This seems to be affecting lots of folks. [This thread]("http://ubuntuforums.org/showthread.php?t=1287153&page=2") claims that [bug #444597]("https://bugs.launchpad.net/ubuntu/+bug/444597") in launchpad has a solution, but I must be too stupid to see it, and the thread is closed so I can't post there.

All my rc and init files seem fine, bootsplash is off, and, of course, there are no useful boot error logs in Karmic.

---

### Post by klausner on 2010-03-09
Bump

---

### Post by registrationsucks322 on 2010-03-23
Fix for me from [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/500520/comments/8 ]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/500520/comments/8")

[INDENT][FONT=Courier New]For some reason i didn't have loopback interface defined in:
/etc/network/[/FONT][FONT=Courier New]interfaces
[/FONT] 
[FONT=Courier New]So i've done:
sudo vim /etc/network/[/FONT][FONT=Courier New]interfaces[/FONT]

[FONT=Courier New]and added:[/FONT][FONT=Courier New]
[/FONT][INDENT][FONT=Courier New]auto lo[/FONT]
[FONT=Courier New] iface lo inet loopback[/FONT]
[/INDENT][FONT=Courier New]
[/FONT]
[FONT=Courier New]I think Ubuntu should have some self testing tool for basic settings. If it is known that some apps do require loopback interface for working (e.g. upstart) then there should be some automatic test tool checking whether the interface exists !! Ther should be some general solution for this kind. Maybe some kind of 'Unit test' tool[/FONT]
[/INDENT]

---

