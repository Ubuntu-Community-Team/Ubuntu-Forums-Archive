---
title: "need help with logrotate"
date: 2012-07-05
forum: General Help
---

### Post by ppqq on 2012-07-05
I put Xubuntu on an old laptop which has to use a wireless adapter card (slot in one) to get internet..
problem is syslog and kern.log get massive from all the connection error messages..

anyway I think I'd like to rotate these logs soon as they hit 1mb so they don't render the laptop unbootable in a few days.  
they generally grow 250mb per day, and without checking and sudo rm they can build up to over 10Gb and that's highly impracticable for the person i need to give the laptop to.

I appended the logrotate.conf file with

/var/log/sys.log {
        rotate 4
        size 1M
        missingok
        notifempty
        compress
        delaycompress
        sharedscripts
        postrotate
                invoke-rc.d rsyslog reload >/dev/null 2>&1 || true
        endscript
}

which I adapted from [http://ubuntuforums.org/showthread.php?t=1830579]("http://ubuntuforums.org/showthread.php?t=1830579")
but sys.log keeps building

so where's it wrong?

thnx for any help

---

### Post by ajgreeny on 2012-07-05
It would be better to get rid of all those error messages that fill up your system, wouldn't it?

Can you find another card which works properly, or troubleshoot the connection errors and get this one working as it should.

What card is it, and have you tried getting it to work better?

---

### Post by SeijiSensei on 2012-07-05
> /var/log/sys.log

The file is named /var/log/syslog without the dot.

---

### Post by alexlpratt on 2012-07-05
> **ajgreeny said:**
> It would be better to get rid of all those error messages that fill up your system, wouldn't it?

Can you find another card which works properly, or troubleshoot the connection errors and get this one working as it should.

What card is it, and have you tried getting it to work better?

Can you give any more explicit detail regarding the actual errors? Also, if you don't plan on getting that fixed, depending on what's doing the logging, you may be able to send the logs to /dev/null or turn them off.

---

### Post by ppqq on 2012-07-06
Ok, firstly sorry, it is syslog and kern.log I am looking at -I pasted a back copy before edit.


in my /etc/logrotate.conf file, i put in exactly


/var/log/syslog {
        rotate 3
        size 5M
        missingok
        notifempty
        compress
        delaycompress
        sharedscripts
        postrotate
                invoke-rc.d rsyslog reload >/dev/null 2>&1 || true
        endscript
}

/var/log/kern.log {
        rotate 3
        size 5M
        missingok
        notifempty
        compress
        delaycompress
        sharedscripts
        postrotate
                invoke-rc.d rsyslog reload >/dev/null 2>&1 || true
        endscript
}


but I think I *misread* the thread where I took that from -is the script for each log meant to go in a log-specific file in /etc/logrotate.d/ ??

I did a tail -n 5000 /var/log/kern.log and syslog and both had the same error line repeating thousands times over which I presume was made on shut-down (as monitoring the log files they don't seem to grow much, then the next boot they are very grown in size -June 30 was the last time I had the laptop on).

Jun 30 20:00:08 d-laptop kernel: [ 3836.009249] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times

it might not be a network card after all.

thanks for the help, I'm learning! but its time-consuming!

---

### Post by steeldriver on 2012-07-06
> **ppqq said:**
> 
I did a tail -n 5000 /var/log/kern.log and syslog and both had the same error line repeating thousands times over which I presume was made on shut-down (as monitoring the log files they don't seem to grow much, then the next boot they are very grown in size -June 30 was the last time I had the laptop on).

Jun 30 20:00:08 d-laptop kernel: [ 3836.009249] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times


it's graphics (dri2) related - there's a fix here that you might want to try

[http://ubuntuforums.org/showpost.php?p=12025605&postcount=11](http://ubuntuforums.org/showpost.php?p=12025605&postcount=11)

---

### Post by ppqq on 2012-07-06
thanks, that's noted and I'm trying that fix

on just one reboot both those logs are under 100kb... so looks good so far.  One more thing fixed its been a good day!

---

