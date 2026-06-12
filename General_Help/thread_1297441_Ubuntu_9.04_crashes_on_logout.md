---
title: "Ubuntu 9.04 crashes on logout"
date: 2009-10-21
forum: General Help
---

### Post by NoTownKasper on 2009-10-21
I've got an interesting issue, every time I try to 'log out' my system bogs down to a standstill leaving me with a black screen that never even tries to return to the login, any ideas what might be wrong, how to check, and perhaps even fix this issue?

---

### Post by cwbar_1 on 2009-10-21
Read through this and see if it helps.
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/107115](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/107115)
Is your video card ATI, and are you using the fglrx driver instead of the ATI restricted driver?

---

### Post by martrn on 2009-10-21
At the location /var/log on your ubuntu system you will or should have a set of log files that you can view.  For a more detailed view of what log files you should look at see : [https://help.ubuntu.com/community/LinuxLogFiles]("https://help.ubuntu.com/community/LinuxLogFiles") !

If you look at syslog  and kern.log (the ones with the most recent date), it should tell you what happened just prior to leavening you at a stand still and leaving you with a black screen.

You can view log files using GUI tools using the GNOME System Log Viewer, click on system-->administration-->systemlog: to view and monitor your system log files.

---

