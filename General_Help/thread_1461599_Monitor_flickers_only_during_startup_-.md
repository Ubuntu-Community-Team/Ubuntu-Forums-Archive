---
title: "Monitor flickers only during startup -"
date: 2010-04-24
forum: General Help
---

### Post by Trueill on 2010-04-24
Hey,

I recently switched to ubuntu from windows 7,so i am a total noob.
I have few queries to ask

My monitor flickers 3-4 times only during startup.I also get some bunch of errors before ubuntu is loaded.I cannot see those error messages because ubuntu is loaded instantly.I only get 1-2 second to read those errors(but i can't read so fast).Can i read them ? How should i stop my monitor to flicker.Also, my postcode shows 00(it used to show FF on windows 7), any ideas why ?

Also can i install any graphics driver ? I read something somewhere and all i have is -

```
lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690 [Radeon X1200 Series] [1002:791e]

```

And i'm on Ubuntu 10.04 LTS - the Lucid Lynx - released in April 2010

Thankyou for helping.

---

### Post by colorlessprism on 2010-04-24
"read something somewhere"...i love it

10.04 LTS has not been released just yet, your using 10.04RC. Lucid Lynx will still be a bit buggy at this point (actually i wouldn't consider it stable until around June, when we have many more people reporting bugs) however, 10.04RC is one of the most stable release candidates thus far so i am pleased. you should post the error codes for all to see, to start System Log Viewer *Click on System > Choose Administration > System Log* or ALT+F2 --> gnome-system-log

log files are typically stored in **/var/log**:
  **/var/log/messages** : General log messages
   **/var/log/boot** : System boot log
   **/var/log/debug** : Debugging log messages
   **/var/log/auth.log** : User login and authentication logs
   **/var/log/daemon.log** : Running services such as squid, ntpd and others log message to this file
   **/var/log/dmesg** : Linux kernel  ring buffer log
   **/var/log/dpkg.log** : All binary package log includes package installation and other information
   **/var/log/faillog** : User failed login log file
   **/var/log/kern.log** : Kernel log file
   **/var/log/lpr.log** : Printer log file
   **/var/log/mail.*** : All mail server message log files
   **/var/log/mysql.*** : MySQL server log file
   **/var/log/user.log** : All userlevel logs
   **/var/log/xorg.0.log** : X.org log file
   **/var/log/apache2/*** : Apache web server log files directory
   **/var/log/lighttpd/*** : Lighttpd web server log files directory
   **/var/log/fsck/*** : fsck command log
   **/var/log/apport.log** : Application crash report / log file

---

### Post by Trueill on 2010-04-24
Which logs should i post ? 

> **colorlessprism said:**
> "read something somewhere"...i love it

10.04 LTS has not been released just yet, your using 10.04RC. Lucid Lynx will still be a bit buggy at this point (actually i wouldn't consider it stable until around June, when we have many more people reporting bugs) however, 10.04RC is one of the most stable release candidates thus far so i am pleased. you should post the error codes for all to see, to start System Log Viewer *Click on System > Choose Administration > System Log* or ALT+F2 --> gnome-system-log

log files are typically stored in **/var/log**:
  **/var/log/messages** : General log messages
   **/var/log/boot** : System boot log
   **/var/log/debug** : Debugging log messages
   **/var/log/auth.log** : User login and authentication logs
   **/var/log/daemon.log** : Running services such as squid, ntpd and others log message to this file
   **/var/log/dmesg** : Linux kernel  ring buffer log
   **/var/log/dpkg.log** : All binary package log includes package installation and other information
   **/var/log/faillog** : User failed login log file
   **/var/log/kern.log** : Kernel log file
   **/var/log/lpr.log** : Printer log file
   **/var/log/mail.*** : All mail server message log files
   **/var/log/mysql.*** : MySQL server log file
   **/var/log/user.log** : All userlevel logs
   **/var/log/xorg.0.log** : X.org log file
   **/var/log/apache2/*** : Apache web server log files directory
   **/var/log/lighttpd/*** : Lighttpd web server log files directory
   **/var/log/fsck/*** : fsck command log
   **/var/log/apport.log** : Application crash report / log file

---

### Post by colorlessprism on 2010-04-25
i would check the boot logs first

---

### Post by veggen on 2010-04-25
Try pressing Pause/Break button to freeze the process and read the error messages.

---

