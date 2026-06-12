---
title: "Service not starting during boot"
date: 2010-03-19
forum: General Help
---

### Post by akernan on 2010-03-19
I'm having a problem getting my MPD service to start during boot. This started a week or so ago.  It's no big deal, just a pain. It start fine when I run the script in a terminal.  I changed the start priority with update-rc.d.  I occasionally get a segfault message in my syslog and messages log.  Not sure what it means.  Can anybody help?

Mar 18 22:44:25 tony-laptop kernel: [ 1244.162897] mpd[3874]: segfault at c00 ip 0806f7d2 sp b6f2a130 error 4 in mpd[8048000+4e000]
Mar 18 22:55:28 tony-laptop kernel: [ 1907.414336] mpd[4759]: segfault at c ip 00194d1d sp b6f9bcd4 error 4 in libpthread-2.10.1.so[18d000+15000]

Thanks.

---

### Post by akernan on 2010-03-20
Can anyone help?  I thought I remember seeing something about this problem but I can't find it.

---

### Post by akernan on 2010-03-21
No one here can help?  I found a post about the problem on Launchpad.net but nobody replied.

---

### Post by mechro on 2010-03-21
I have no idea but does this help?...

[https://help.ubuntu.com/community/MPD](https://help.ubuntu.com/community/MPD)

---

### Post by akernan on 2010-03-21
I saw that, it didn't fix my problem.

---

