---
title: "Problems with boot"
date: 2006-03-28
forum: General Help
---

### Post by Jazzinghen on 2006-03-28
Hi.
Yesterday Ubuntu started to freeze during the startup when it tries to start the System Log Daemon.
The fact is that the machine doesn't reboot if I wait, like any other case I've seen on this forum, but GNOME and everything else start.
So I've thought to have a look through /var/log/messages and I've found that this file is, like, 2GB (Is that normal?). The possibility is that this file is too big, si the syslogd have to read through all and so it hangs up for many minutes (10).
The other problem is that in the message file the last... 680000 lines (I've discovered the number of lines using tail) are all messages telling me that there is a problem with txdesc or txdull (Sometimes the line is only "ull" "[some numbers]ull" "[some numbers] dull" and so on) and that they have a BUG.
Now. How can I fix this problem? Because it's really annoying and I need the system. Yesterday I've finnaly managed to completely install for the third thime the system, so it would be a shame if I'd need to reinstall the system from start again...
Thanks.
(Ubuntu Breezy Badger 5.10, i386)

---

### Post by trent dillman on 2006-03-28
Wow...my /var/log/messages is only 4K!!!

Back up the old and touch the new until you figure it out...

```

sudo mv /var/log/messages /var/log/messages.backup
sudo touch /var/log/messages

```

Take note that this is a temporary fix. Sounds like a bug to me.

What network devices/drivers are you using?

---

### Post by Jazzinghen on 2006-03-28
[QUOTE=trent dillman]Wow...my /var/log/messages is only 4K!!!

Back up the old and touch the new until you figure it out...

```

sudo mv /var/log/messages /var/log/messages.backup
sudo touch /var/log/messages

```

Take note that this is a temporary fix. Sounds like a bug to me.

What network devices/drivers are you using?[/QUOTE]
I'm using an USRobotics WLAN Card (Turbo) and it works thanks to the restricted nic modules.

---

