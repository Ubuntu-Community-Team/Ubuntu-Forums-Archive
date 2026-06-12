---
title: "Run script as root upon login"
date: 2012-03-23
forum: General Help
---

### Post by Warthaug on 2012-03-23
I have an unusual problem.  I am configuring a computer to access a remote server at boot.  Due to various issues this cannot be done via fstab, and instead must be done ~10 seconds _after_ a user has logged in (using mount.cifs).

I have worked around this using a script; using the sleep command to force a delay, followed by the mount.cifs command, a check for the connection (and if failed, a second attempt at connecting after yet another sleep command).

The problem I am having is that the script must be run as root (it requires the use of sudo)  Because reboots/logins are done unattended it must be run as root, rather than asking for input using gksudo.  At the moment I've simply added it to the "starup applications" menu; which obviously does not work.

How do I get around this?  The script is already owned/grouped to root...that didn't work either.

Thanx

Bryan

---

### Post by Cheesemill on 2012-03-23
Anything that you put in /etc/rc.local will be run with root privileges when you boot.
Just call the script from there.

---

### Post by Habitual on 2012-03-23
> **Cheesemill said:**
> .../etc/rc.local will be run with root privileges when you boot.

"sudo" command won't be necessary in a script used via /etc/rc.local

---

### Post by Warthaug on 2012-03-23
> **Cheesemill said:**
> Anything that you put in /etc/rc.local will be run with root privileges when you boot.
Just call the script from there.
But having it run at boot doesn't solve my problem - it needs to run several seconds after log-in.  I started my attempts with it running at boot, to no avail.

Bryan

---

### Post by Toz on 2012-03-23
How about autofs? Once set up, it creates the session and accesses the share when required and automatically disconnects after a point of inactivity. You won't have to worry about the delay as the share will be accessed when needed. I've been using autofs to access my cifs shares for a while now and its been working fine.

See: [https://help.ubuntu.com/community/Autofs]("https://help.ubuntu.com/community/Autofs")

EDIT: I find the **--ghost** option in /etc/auto.master helpful because it creates the skeleton directories for the shares so that you can just click on them (or move into them) to establish the connection:
```
/data /etc/auto.home --timeout=60 --ghost
```

---

