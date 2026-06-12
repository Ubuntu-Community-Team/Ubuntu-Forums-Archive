---
title: "rsyslogd problems in natty. Can't send log messages to console."
date: 2011-05-16
forum: General Help
---

### Post by ubudillo on 2011-05-16
Hello forum, after upgrading to 11.04, natty, I have a problem with rsyslogd.

In previous releases I went to:

/etc/rsyslog.d/50-default.conf

and uncommented the lines under comment:

# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.

This was redirecting the log messages to a console I could get to via Ctrl-Alt-Fwhatever.

In natty, this no longer works. When I switch to the relevant console I get a blank screen with a blinking cursor.

The file /etc/rsyslog.d/50-default.conf still exists. A new arrival is also 50-default.conf.ucf-dist which, as far as I can tell is a clone and which I have also modified like 50-default.conf.

The file /etc/rsyslog.conf (configuration file for rsyslogd) exists and its last line reads:

$IncludeConfig /etc/rsyslog.d/*.conf

which presumably should force rsyslogd to read 50-default.conf at startup.

Looking at the running processes I can see that rsyslogd runs.

Any ideas what has changed?

---

### Post by skidmarq on 2011-05-17
I'll second the above -- just ran into the same problem here.

---

### Post by Shdwdrgn on 2011-07-28
Same here - just upgraded a system from maverick to natty.  Had rsyslog echoing the syslog output to /dev/tty12.  After the upgrade and reboot, I no longer get anything on tty12.  It's disappointing to see there's been no updates on this thread since May, hopefully someone has found a solution by now?

---

### Post by ubudillo on 2011-07-29
I just noticed something very interesting. I have two user accounts on my laptop and when I 'm logged into one of the two (the one I hardly ever use which is why I didn't realise before), I do get the messages on tty12. I find this very strange, I 'd have thought the logging would be completely independent of whoever user is logged in or not. Can anyone suggest what kind of differences in the two accounts I can look at to see why that might be?

---

### Post by ubudillo on 2011-08-04
Hello again, got a friend to find a workaround for me. It seems there's a permissions problem and syslogd is no longer allowed to play with tty12.

The following code should sort it out:

```
sudo cat <<EOF | tee -a /etc/udev/rules.d/40-tty-permissions.rules
KERNEL=="tty12", GROUP="syslog", MODE="0620"
EOF
sudo update-initramfs -u -k all
```While this code should make it work for your current session (otherwise it will take effect after restarting):

```
sudo chgrp syslog /dev/tty12
sudo service rsyslog restart
```Of course, you have to make sure that you are directing output to tty12 by uncommenting (removing the # signs from) the following lines in file */etc/rsyslog.d/50-default.conf* :


> # I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
daemon,mail.*;\
        news.=crit;news.=err;news.=notice;\
        *.=debug;*.=info;\
        *.=notice;*.=warn       /dev/tty12Please notice that here I direct output to tty12, if I remember rightly, the original file has tty8. So, if you want to use tty8 (or tty<whatever>) instead of tty12, make sure you edit the first chunk of code to read tty8 where it currently reads tty12, i.e. change **KERNEL=="tty12"** to **KERNEL=="tty8"**

---

