---
title: "Risk of Server Upgrade to 9.10 from 9.04"
date: 2009-11-02
forum: General Help
---

### Post by zzzBrett on 2009-11-02
I have a server that I have remote access to via SSH that I was considering upgrading to 9.10.  However, if something goes wrong, I won't have direct access to it to fix it.

Should I assume I'll be able to handle any problems remotely, or is this unlikely? --It's ok if it does go down, i'd just rather it not :)

Also, what would the command be to upgrade it strictly through ssh?

---

### Post by slakkie on 2009-11-02
See my sig, do-release-upgrade would be your friend.

It will start another sshd on some high port in case of..

---

### Post by zzzBrett on 2009-11-02
I broke it :/

Please see post: [http://ubuntuforums.org/showthread.php?t=1312037](http://ubuntuforums.org/showthread.php?t=1312037)

---

