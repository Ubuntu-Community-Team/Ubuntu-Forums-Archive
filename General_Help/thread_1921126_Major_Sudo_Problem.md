---
title: "Major Sudo Problem"
date: 2012-02-06
forum: General Help
---

### Post by dataessa on 2012-02-06
Hi there! 

Guys, 

My situation is problematic. (hopefully you won't think so).

I had problems with my sudo (*sudo must be setuid*)... I then fooled around with the Live CD and solved the problem, but then I got other security problems, and, for instance, had suddenly no access to my own files, and my virtualbox was also impossible to access due to a problem (superhardening and different root or something). 
Then I fooled around again with the Live System and with the ```
chmod -R 777 /usr/
``` and ended up have the same problem I started with. 

The last thing I tried to do:
Through ```
chroot
``` per Live CD I managed to get to my system, and tried to **sudo** a chown to regain permissions, but I have no permissions to sudo (sudo: could not resolve to sudo ubuntu), then I logged in as Daniel (my computer name) and I got a *sudo must be setuid *again!!!! 

I have no idea what to do. Reinstalling would not be so much easier, sind I have files inside my virtualbox, that can go lost in any way and my computer was completely customised...

Please, is there anyone with enough kindness to help me recover my system? Every tip counts! 
Thank you guys in advance for reading this thread till here!


](*,)

ps: although it may not sound so, I'm kind of a beginner. just did my research before deciding to bother you guys, maybe that's been the biggest mistake: I shouldve asked for advice before messing up my ubuntu.

---

### Post by dargaud on 2012-02-06
> I had problems with my sudo (sudo must be setuid)...
Err, why did you have that problem. Sudo should work from the start unless your user is not in the 'sudo' or 'admin' group.
```
$ grep "admin\|sudo" /etc/group
sudo:x:27:
lpadmin:x:115:userone,usertwo
admin:x:117:userone

```
If you've messed up your files. Boot from livecd, copy /usr/bin/sudo (and possibly other files you've messed up with) from the CD onto your mounted partition and edit /etc/group to add your username to the admin line. That's about all there should be to it.

---

