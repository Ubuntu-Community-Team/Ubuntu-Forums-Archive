---
title: "Can I make it so one user can always edit/see/delete another users files?"
date: 2010-11-17
forum: General Help
---

### Post by strider3700 on 2010-11-17
I have deluge setup as it's own user on my machine.  It writes it's files to my regular users home folder in two different folders, Logs and torrents.    The issue is they come in as read only so when I want to clear the log or move the files I have to chmod them or do it with sudo.    chmod -R works great until a new file is created and it goes back to read only.

Is there a way to change it so my regular user account always has permissions to do whatever to the deluge files?

---

### Post by Cas07 on 2010-11-19
I think you are looking for something like this:

[http://ubuntuforums.org/showthread.php?t=1400084](http://ubuntuforums.org/showthread.php?t=1400084)

---

### Post by KeyserSoze93 on 2010-11-19
> **Caos said:**
> I think you are looking for something like this:

[http://ubuntuforums.org/showthread.php?t=1400084](http://ubuntuforums.org/showthread.php?t=1400084)

+1 for Access Control Lists

---

