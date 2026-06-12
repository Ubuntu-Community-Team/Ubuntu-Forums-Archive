---
title: "Help!"
date: 2011-05-05
forum: General Help
---

### Post by MacsFromGS on 2011-05-05
Hi, i am trying to get my website setup on my VPS and i keep seeing this when i try to start mysql 
```
macs@li272-229:~$ service mysql start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.15                                             " (uid=1000 pid=8692 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="                                             Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (                                             uid=0 pid=1 comm="/sbin/init"))
macs@li272-229:~$
```
what do i do :(
please help thanks

---

### Post by r-senior on 2011-05-05
Are you logged in as root when you do that? You normally need to use:

```
sudo service <name> start
```

to start a service.

---

### Post by MacsFromGS on 2011-05-05
All i see is 
```
root@li272-229:~# service mysql restart


```
then i have to restart putty :S

---

