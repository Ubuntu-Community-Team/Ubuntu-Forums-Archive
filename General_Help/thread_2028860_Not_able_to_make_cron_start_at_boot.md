---
title: "Not able to make cron start at boot"
date: 2012-07-18
forum: General Help
---

### Post by agentguerry on 2012-07-18
Hi,

Thanks for reading.  I'm currently still searching for an answer to this.

I am running 10.04, and for some reason when I try to set up cron to run at boot I get errors.

I have tried using chkconfig and update-rc.d
I have uninstalled chkconfig/cron, and reinstalled them.

This is the error I get when running "chkconfig cron on"

root@tarantula:/etc/rc3.d# chkconfig cron on
insserv: warning: script 'freenx-server' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'console-setup' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-stop' missing LSB tags and overrides
insserv: warning: script 'acpi-support' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: There is a loop between service rsyslog and pulseaudio if stopped
insserv:  loop involving service pulseaudio at depth 3
insserv:  loop involving service rsyslog at depth 2
insserv:  loop involving service udev at depth 1
insserv:  loop involving service umountnfs at depth 5
insserv: There is a loop between service rsyslog and pulseaudio if stopped
insserv: exiting now without changing boot order!
/sbin/insserv failed, exit code 1

Any help is appreciated!

---

### Post by agentguerry on 2012-07-19
ending up using sysv-rc-conf.

not sure why all of a sudden chkconfig and update-rc.d are acting up.


[http://ubuntuforums.org/showthread.php?t=1365074](http://ubuntuforums.org/showthread.php?t=1365074)

---

