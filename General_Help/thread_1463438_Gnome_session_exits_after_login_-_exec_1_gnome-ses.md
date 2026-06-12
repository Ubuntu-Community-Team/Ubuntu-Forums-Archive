---
title: "Gnome session exits after login - exec: 1: gnome-session: not foundt"
date: 2010-04-26
forum: General Help
---

### Post by rwg1989 on 2010-04-26
Hello -

Just thought I would share a problem I encounter (self induced) and then solved.

After installing some software and editing the /etc/environment file, I was no longer able to login to the workstation.

After restarting my machine, and then logging in with any user, the GNOME session would fail to start, returning fairly immediately back to the main login screen.

Booting from a 9.10 CD-ROM image, I was able top mount the system volume and troubleshoot.  In the /home/<user> folder, the file .xsession-errors contained the following:

```
$ cat .xsession-errors

/etc/gdm/Xsession: Beginning session setup...
/etc/profile.d/speechd-user-port.sh: 1: getent: not found
/etc/profile.d/speechd-user-port.sh: 1: cut: not found
/etc/profile.d/speechd-user-port.sh: 1: expr: not found
/etc/profile: 26: id: not found
[: 26: Illegal number: 
/etc/gdm/Xsession: 197: ls: not found
/etc/gdm/Xsession: ssh-agent not found!
/etc/gdm/Xsession: Setup done, will execute: gnome-session
exec: 1: gnome-session: not found


```

Eventually, I found that I had a typo in the /etc/environment file that was corrupting the PATH variable.

My problem was solved by correcting the /env/environment variable.

---

