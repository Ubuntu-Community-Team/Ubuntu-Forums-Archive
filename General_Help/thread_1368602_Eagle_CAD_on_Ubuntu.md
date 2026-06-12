---
title: "Eagle CAD on Ubuntu"
date: 2009-12-30
forum: General Help
---

### Post by karl303 on 2009-12-30
Hi,

I'm new here, and ran into an interesting problem while trying to run Eagle PCB on Ubuntu.

Here is a little bit of info on my system:
HP G70-463CL laptop; dual booting Ubuntu 9.10 and Windows 7.

I recently installed Eagle 5.6.0 and am experiencing a problem where, at seemingly random intervals, I am returned to the Ubuntu log-in screen and all of my programs are closed without saving (very annoying).  Interestingly, my SSH connection to the server at work remains alive and well.  This problem has only been seen when I am running Eagle.  Other programs like Firefox and Octave run without any trouble.

At the suggestion of a coworker, I checked out the messages and system log files at /var/log but there is nothing there that jumps out at me as being an obvious clue about what might be going on.

Here is a snippet from the syslog file when one of these crashes/log-outs occurred:
```
Dec 30 18:43:45 karl-ubuntu-mobile wpa_supplicant[1068]: CTRL-EVENT-SCAN-RESULTS 
Dec 30 18:44:29 karl-ubuntu-mobile kernel: Kernel logging (proc) stopped.
Dec 30 18:45:04 karl-ubuntu-mobile kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Dec 30 18:45:04 karl-ubuntu-mobile rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="876" x-info="http://www.rsyslog.com"] (re)start
Dec 30 18:45:04 karl-ubuntu-mobile rsyslogd: rsyslogd's groupid changed to 102
Dec 30 18:45:04 karl-ubuntu-mobile rsyslogd: rsyslogd's userid changed to 101
Dec 30 18:45:04 karl-ubuntu-mobile NetworkManager: <info>  starting...
```In the 5 seconds following 18:45:04, there are about 1000 more entries into the syslog which appear to me to be related to the system starting up.

Here are some of the corresponding entries around the crash for the messages log file:
```
Dec 30 18:15:26 karl-ubuntu-mobile kernel: [12780.181185] [drm] TV-20: set mode NTSC 480i 0
Dec 30 18:44:29 karl-ubuntu-mobile kernel: Kernel logging (proc) stopped.
Dec 30 18:45:04 karl-ubuntu-mobile kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Dec 30 18:45:04 karl-ubuntu-mobile rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="876" x-info="http://www.rsyslog.com"] (re)start
```Any thoughts or suggestions for diagnosing this further?

Thanks!

---

