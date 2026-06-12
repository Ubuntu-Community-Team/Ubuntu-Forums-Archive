---
title: "logging install/remove commands"
date: 2012-01-29
forum: General Help
---

### Post by George Heine on 2012-01-29
I there a way to create a system log which automatically:
    1) records the time and options of every command beginning "sudo aptitude"
    2) records the initial message sent by aptitude (e.g.,"the following new packages will be installed...")
    3) log is in a secure location (e.g., /var/log) and can be read, but not written to or deleted by ordinary users

Or does a log like this already exist?

Am using Ubuntu 9.10, 10.04, and 11.04 with Gnu bash.

thanks for your help

---

### Post by cryptotheslow on 2012-01-29
Anything executed with sudo will be logged in /var/log/auth.log
Package manager actions are logged in /var/log/dpkg.log

There are also apt logs at:
/var/log/apt/term.log
/var/log/apt/history.log


None of these logs can be changed / deleted without elevated privilege as they are owned by root - but they can be read by any user.

Have a shuffle through them with a text editor or cat - I'm sure between them you can get what you need.

---

