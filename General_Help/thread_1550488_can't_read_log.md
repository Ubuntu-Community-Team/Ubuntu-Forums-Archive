---
title: "can't read log"
date: 2010-08-11
forum: General Help
---

### Post by duke.tim on 2010-08-11
I am receiving this error when I attempt to open system logs, why? can I fix it... maybe the privilages got messed up i'll need to check, but it happened shortly after accidentally loging into guest.

```

Could not open the following files:
/var/log/ufw.log.1: Error stating file '/var/log/ufw.log.1': No such file or directory
/var/log/auth.log.1: Error stating file '/var/log/auth.log.1': No such file or directory
/var/log/daemon.log.1: Error stating file '/var/log/daemon.log.1': No such file or directory
/var/log/kern.log.1: Error stating file '/var/log/kern.log.1': No such file or directory
/var/log/debug.1: Error stating file '/var/log/debug.1': No such file or directory
/var/log/messages.1: Error stating file '/var/log/messages.1': No such file or directory
/var/log/pm-powersave.log.1: Error stating file '/var/log/pm-powersave.log.1': No such file or directory
/var/log/pm-suspend.log.1: Error stating file '/var/log/pm-suspend.log.1': No such file or directory
/var/log/dpkg.log.1: Error stating file '/var/log/dpkg.log.1': No such file or directory
/var/log/popularity-contest.0: Error stating file '/var/log/popularity-contest.0': No such file or directory

```

---

### Post by duke.tim on 2010-08-12
Well I checked and the files aren't there. The normal logs are there so i'm wondering if anyone knows whats going on....

---

### Post by earthpigg on 2010-08-12
what makes you think the .1 files ought to exist at all?

.log files are created. as they get large, .log.1, .log.2, .log.n log files are created to archive the older data.

for example:

i have a dpkg.log, a dkpg.log.1, .2.gz, and .3.gz. the stuff in .log is recent. .1 is older stuff. .2.gz is even older, and .3.gz is from the time immediately around when i first installed ubuntu 10.04.

i do not have, however, any ufw.log files aside from that one. no ufw.log.1, or anything else.

if this is a brand new Ubuntu install, it's possible you do not have a single log.1 file for anything.

---

### Post by duke.tim on 2010-08-13
The problem isn't so much that they aren't there but that the "log file viewer" gives me this error every time I look in it. it's not crippling so it's not super urgent but it is annoying. and why would the system suddenly delete my logs, I didn't delete them....

---

### Post by Rubi1200 on 2010-08-13
Can you open the logs in the terminal?

For example,

```
gedit /var/log/auth.log
```

If you can and there are no error messages, the problem may be with the Log File Viewer or part of the package it belongs to.

---

### Post by duke.tim on 2010-08-14
I can see the logs in the shell and in log viewer. I cannot see the deleted logs in either. I tried reinstalling gnome-utils but that hasn't fixed the issue maybe I'll just place "place-holder" files into the directory.

okay I tried it and this seemed to work still bewildered on why the logs got deleted in the first place....

```
duke@duke-laptop:/var/log$ sudo touch auth.log.1
```
and on and on for the rest of the trouble some logs

---

### Post by duke.tim on 2010-08-14
Boy I feel stupid I just figured out what deleted the logs it was Bleach Bit](*,) , thanks everyone for the suggestions

---

