---
title: "Karmic, gksudo and runas_default"
date: 2009-12-13
forum: General Help
---

### Post by misiu369 on 2009-12-13
I've been using this solution:
[http://ubuntuforums.org/showthread.php?t=181877](http://ubuntuforums.org/showthread.php?t=181877)
to have a different login and sudo passwords.

Basically, I've set in sudoers the runaspw and runas_default options. It asks me for another users password when I run sudo. 

It worked well in Jaunty (9.04), but after upgrading to Karmic (9.10) gksudo stopped working. Testing uncovered that the "runas_default" option in "defaults" part of the sudoers file is responsible for that.

gksudo works as expected:
- with runaspw but without the runas_default set in sudoers (asks for root's passwd)
- with neither runaspw nor runas_default set in sudoers (asks for my passwd)
- when executed with "-u username" option (asks for that users passwd)

running "gksudo -d gedit" exports this:
```
No ask_pass set, using default!
xauth: /tmp/libgksu-YpyHeF/.Xauthority
STARTUP_ID: gksudo/gedit/2999-0-mymachine_TIME295802
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: gedit
buffer: -sudo: unable to cache uid, already exists-
buffer: --
buffer: --
buffer: --
[..]
buffer: --
buffer: --
buffer: --
brute force GNOME_SUDO_PASS ended...
No password prompt found; we'll assume we don't need a password.
xauth: /tmp/libgksu-YpyHeF/.Xauthority
xauth_env: /var/run/gdm/auth-for-myusername-Nrgqpk/database
dir: /tmp/libgksu-YpyHeF
```

I've been searching for two days for any solution, but I found no mention of it anywhere. Can anybody help or point me in any direction? Does anybody know what changed in gksu lately?

I've seen the new gksu-polkit in repo, but it has broken dependencies (there's no libgee0, there's a libgee1 now). Additionally I'd have to find a way to put a new username (the one with my sudo password) into the polkit list.

---

