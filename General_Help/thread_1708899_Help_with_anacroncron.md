---
title: "Help with anacron/cron"
date: 2011-03-17
forum: General Help
---

### Post by teocomi on 2011-03-17
Hello, excuse me if this is a very stupid question but I'm very new to Linux and I couldn't figure out the problem mysef (even after googleing a lot!).

I just would like to have two script run every day. If the pc is OFF, I would like to have them run as soon as the pc turns ON (but they should not accumulate!).. So I read somewere that I have to use anacron, and that I simply need to put the scripts in cron.daily folder... But they are not executed!

[IMG]http://i.imgur.com/3Gke1.jpg[/IMG]

If I test with:

```
run-parts –test /etc/cron.daily
```

they do appear in the list...

---

### Post by Cheesehead on 2011-03-17
The most likely causes of cron-script failure are:

1) Need to use full paths in the script.  For example '/usr/bin/foo' instead of just 'foo'. Cron runs in a much more limited environment than a user's typical terminal session. It can do just about anything, but you must be explicit in the instructions.

2) Needs environment variables that were not declared. For example, 'DISPLAY=:0.0' to refer to your monitor.

It's pretty much those two most of the time.
Check syslog: 'cat /var/log/syslog | grep cron'.  Are you getting any error messages from cron or anacron?  

If you need more help, please post the scripts.

---

### Post by blueridgedog on 2011-03-17
Do you have some error checking built into the scripts so that you know they are not running?  Can you run them manually and get the results you want?  Are there any log entries relative to the scripts that might give you the reason for the failure?

```
sudo grep CRON /var/log/syslog
```

---

### Post by teocomi on 2011-03-22
Hi guys! Pardon me, it was all my fault (obviously)..
The scripts were run correctly, but since they were run as root, it didn't have enough permissions to acheive the task (backing up remote pc via ssh), so now I just needed to add the permissions for the root user and everything is fine!


Thanks anyway, learning is good!

---

