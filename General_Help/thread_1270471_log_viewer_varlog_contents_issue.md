---
title: "log viewer var/log contents issue"
date: 2009-09-19
forum: General Help
---

### Post by bladerunner6 on 2009-09-19
I deleted the files in the var/log folder thinking to reduce down the number of log files in log viewer, i realised i needed to recreate them
so i used the command sudo touch dmesg etc.

but now i see that some are blank and not showing me the right info

am using karmic alpha 6

---

### Post by Liolikas on 2009-09-19
you delete them - they they reappear with new info and old info is lost. If you recreted them with sudo so no good possibly too strict permissions you have to sudo rm them and they should reappear themselves.

---

### Post by bladerunner6 on 2009-09-20
i deleted them but not all were recreated
i get the following missing files in log file viewer

/var/log/auth.log: Error stating file '/var/log/auth.log': No such file or directory
/var/log/daemon.log: Error stating file '/var/log/daemon.log': No such file or directory
/var/log/kern.log: Error stating file '/var/log/kern.log': No such file or directory
/var/log/lpr.log: Error stating file '/var/log/lpr.log': No such file or directory
/var/log/dpkg.log: Error stating file '/var/log/dpkg.log': No such file or directory
/var/log/user.log: Error stating file '/var/log/user.log': No such file or directory
/var/log/Xorg.3.log: Error stating file '/var/log/Xorg.3.log': No such file or directory
/var/log/Xorg.2.log: Error stating file '/var/log/Xorg.2.log': No such file or directory
/var/log/Xorg.1.log: Error stating file '/var/log/Xorg.1.log': No such file or directory
/var/log/syslog: Error stating file '/var/log/syslog': No such file or directory
/var/log/jockey.log: Error stating file '/var/log/jockey.log': No such file or directory
/var/log/mail.log: Error stating file '/var/log/mail.log': No such file or directory
/var/log/mail.info: Error stating file '/var/log/mail.info': No such file or directory
/var/log/mail.warn: Error stating file '/var/log/mail.warn': No such file or directory
/var/log/mail.err: Error stating file '/var/log/mail.err': No such file or directory
/var/log/debug: Error stating file '/var/log/debug': No such file or directory
/var/log/messages: Error stating file '/var/log/messages': No such file or directory
/var/log/Xorg.4.log: Error stating file '/var/log/Xorg.4.log': No such file or directory
/var/log/Xorg.5.log: Error stating file '/var/log/Xorg.5.log': No such file or directory
/var/log/gufw_log.txt: Error stating file '/var/log/gufw_log.txt': No such file or directory
/var/log/dmesg: Error stating file '/var/log/dmesg': No such file or directory
/var/log/dmesg.0: Error stating file '/var/log/dmesg.0': No such file or directory
/var/log/boot: Error stating file '/var/log/boot': No such file or directory
/var/log/bootstrap.log: Error stating file '/var/log/bootstrap.log': No such file or directory
/var/log/btmp: Error stating file '/var/log/btmp': No such file or directory
/var/log/fontconfig.log: Error stating file '/var/log/fontconfig.log': No such file or directory
/var/log/pycentral.log: Error stating file '/var/log/pycentral.log': No such file or directory

---

### Post by Liolikas on 2009-09-20
Like normal that you do not have something like:
/var/log/Xorg.5.log
It will appear after 5 boots.

What is your log viewer name? It is far from best one.

---

### Post by bladerunner6 on 2009-09-20
Log Viewer 2.27.91
is the log viewer in gnome.

question is how do i recreate the kern.log and dmesg etc with the right permissions if sudo method is not right


thanks

---

