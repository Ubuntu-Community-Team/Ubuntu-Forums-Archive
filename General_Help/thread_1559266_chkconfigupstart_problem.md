---
title: "chkconfig/upstart problem"
date: 2010-08-23
forum: General Help
---

### Post by JasonSwett on 2010-08-23
My overall goal is to get postfix working. What I'm trying to do right now is stop sendmail.

When I run sudo /sbin/chkconfig sendmail off, I get this:
```

The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-stop' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hostname' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'mysql' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-splash' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'atd' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'procps' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'rsyslog' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dmesg' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cron' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev-finish' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'console-setup' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-log' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'vsftpd' missing LSB tags and overrides
insserv: There is a loop between service rsyslog and apache2 if stopped
insserv:  loop involving service apache2 at depth 3
insserv:  loop involving service rsyslog at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop between service apache2 and rsyslog if stopped
insserv: exiting now without changing boot order!
/sbin/insserv failed, exit code 1

```
Any idea why this is happening?

Thanks,
Jason

---

### Post by Rubi1200 on 2010-08-23
Ubuntu is moving more and more towards upstart:

[http://upstart.ubuntu.com/index.html](http://upstart.ubuntu.com/index.html)

The way to stop/start/restart services (assuming it is something normally in /etc/init.d/):

```
service program_name start/stop/restart
```e.g. ```
service denyhosts stop
``` (just an example)
Hope this helps.

---

### Post by JasonSwett on 2010-08-23
Yes, that worked.

I'm sorry but I didn't word my original post very well. I'm following the instructions [here]("http://www.linuxtopia.org/HowToGuides/linux_email_setup_guide/linux_postfix_preinstall.html") and I'm actually past the "stop" step. I'm at the chkconfig step. Any idea why I'm getting the errors I'm getting there?

---

### Post by Rubi1200 on 2010-08-24
I am not at my regular computer right now, but I believe you need to run ```
initctl list
``` to see what is running and the status of each service.

---

### Post by JasonSwett on 2010-08-24
Hmm, I don't understand what that would do for me.

Running /sbin/chkconfig --list | grep sendmail works just fine. It's the /sbin/chkconfig sendmail off step that's throwing errors.

---

### Post by Rubi1200 on 2010-08-24
> **JasonSwett said:**
> Hmm, I don't understand what that would do for me.

Running /sbin/chkconfig --list | grep sendmail works just fine. It's the /sbin/chkconfig sendmail off step that's throwing errors.
I understood that chkconfig is no longer the way to go and that running 
```
initctl list
```will give you a list of services, including, I assume, sendmail, which you can then either stop/start/restart.

I don't use sendmail or postfix, so as far as that is concerned I am not sure what to tell you.

---

### Post by JasonSwett on 2010-08-25
I just want to be able to run "chkconfig sendmail off" without getting errors. Any other ideas?

---

### Post by sisco311 on 2010-08-25
> **JasonSwett said:**
> I just want to be able to run "chkconfig sendmail off" without getting errors. Any other ideas?

You are following an outdated tutorial. chkconfig is deprecated. 

But, sendmail is still started by a System-V style init script, so you could use update-rc.d to disable it:
```
sudo update-rc.d -f sendmail remove
```
To re-enable it, run:
```
sudo update-rc.d sendmail defaults 21 19
```

---

### Post by JasonSwett on 2010-08-26
That worked. Thanks.

---

### Post by Justin Buser on 2012-06-25
> **JasonSwett said:**
> I just want to be able to run "chkconfig sendmail off" without getting errors. Any other ideas?

```
chkconfig sendmail off &> /dev/null
```

Of course it doesn't really matter WHAT output you get from chkconfig if sendmail is being started by upstart. Put:
```
DISABLED=1
```
at the top of /etc/init/sendmail if you want to disable the upstart job.

---

### Post by oldos2er on 2012-06-25
Old thread closed.

---

