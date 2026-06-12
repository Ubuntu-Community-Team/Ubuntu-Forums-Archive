---
title: "Crash Report at every boot"
date: 2012-07-10
forum: General Help
---

### Post by Toriam on 2012-07-10
EVery time I boot my computer, I get a crash report. I just clean installed 12.04. It happens on both users. It seems to be the standard one. Also, with most boots I get a message during the start screen about/var/log (?)/cryptswap. Im trying to catch that one. Will post again once I get the text. The computer behaves normally.
Thanks for reading!

---

### Post by Rodney9 on 2012-07-10
Check your log files for errors, probably your boot log

View log files in Ubuntu Linux
by VIVEK GITE 

Q. Can you explain me log files in Ubuntu Linux and how do I view logs?

A. All logs are stored in /var/log directory under Ubuntu (and other Linux distro).

Linux Log files and usage

=> /var/log/messages : General log messages

=> /var/log/boot : System boot log

=> /var/log/debug : Debugging log messages

=> /var/log/auth.log : User login and authentication logs

=> /var/log/daemon.log : Running services such as squid, ntpd and others log message to this file

=> /var/log/dmesg : Linux kernel ring buffer log

=> /var/log/dpkg.log : All binary package log includes package installation and other information

=> /var/log/faillog : User failed login log file

=> /var/log/kern.log : Kernel log file

=> /var/log/lpr.log : Printer log file

=> /var/log/mail.* : All mail server message log files

=> /var/log/mysql.* : MySQL server log file

=> /var/log/user.log : All userlevel logs

=> /var/log/xorg.0.log : X.org log file

=> /var/log/apache2/* : Apache web server log files directory

=> /var/log/lighttpd/* : Lighttpd web server log files directory

=> /var/log/fsck/* : fsck command log

=> /var/log/apport.log : Application crash report / log file

To view log files at shell prompt

Use tail, more, less and grep command.
tail -f /var/log/apport.log
more /var/log/xorg.0.log
cat /var/log/mysql.err
less /var/log/messages
grep -i fail /var/log/boot


Rodney

---

### Post by Toriam on 2012-07-11
I was looking at apport.log.1 and found this (apport.log was empty):

ERROR: apport (pid 22159) Fri Jul  6 16:03:51 2012: called for pid 21914, signal 11
ERROR: apport (pid 22159) Fri Jul  6 16:03:51 2012: executable: /usr/lib/i386-linux-gnu/tumbler-1/tumblerd (command line "/usr/lib/i386-linux-gnu/tumbler-1/tumblerd")
ERROR: apport (pid 22159) Fri Jul  6 16:03:51 2012: gdbus call error: Error: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

ERROR: apport (pid 22159) Fri Jul  6 16:03:51 2012: debug: session gdbus call: 
ERROR: apport (pid 22159) Fri Jul  6 16:03:51 2012: apport: report /var/crash/_usr_lib_i386-linux-gnu_tumbler-1_tumblerd.1000.crash already exists and unseen, doing nothing to avoid disk usage DoS
ERROR: apport (pid 22189) Fri Jul  6 16:04:52 2012: called for pid 22164, signal 11
ERROR: apport (pid 22189) Fri Jul  6 16:04:52 2012: executable: /usr/lib/i386-linux-gnu/tumbler-1/tumblerd (command line "/usr/lib/i386-linux-gnu/tumbler-1/tumblerd")
ERROR: apport (pid 22189) Fri Jul  6 16:04:52 2012: gdbus call error: Error: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

ERROR: apport (pid 22189) Fri Jul  6 16:04:52 2012: debug: session gdbus call: 
ERROR: apport (pid 22189) Fri Jul  6 16:04:52 2012: apport: report /var/crash/_usr_lib_i386-linux-gnu_tumbler-1_tumblerd.1000.crash already exists and unseen, doing nothing to avoid disk usage DoS

But i see everything is july 6th, and his is an everyday occurance. I'll keep looking, but if anyone can decode this that'll be great!

---

### Post by Toriam on 2012-07-11
:popcorn:

---

