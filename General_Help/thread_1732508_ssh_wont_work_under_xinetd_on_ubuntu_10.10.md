---
title: "ssh wont work under xinetd on ubuntu 10.10"
date: 2011-04-18
forum: General Help
---

### Post by cryptoboss on 2011-04-18
Hello everybody , this my first post on the forum , im so glade to be here with you .
So my xinetd configuration is :

/etc/xinetd.d/ssh
```
service ssh
{
 disable = no
 socket_type     = stream
 protocol     = tcp
 port            = 2022
 wait         = no
 user         = root
 server         = /usr/sbin/sshd
 server_args     = -i -u0 -4 -f /etc/ssh/sshd_config
 log_on_success += HOST PID EXIT DURATION TRAFFIC
 log_on_failure += HOST
 only_from     = 192.168.0.0/16
 access_times   = 08:00-18:00    
}
```/etc/xinetd.conf
```
defaults
{

instances = 60
log_type = SYSLOG daemon
log_on_success = HOST PID
log_on_failure = HOST
cps = 25 30

}

includedir /etc/xinetd.d
```After a xinted restart , ssh still able to connect from outside from any IP address and at any time?? what should I do?? Iv seen that i have to disable the default sshd , but how ??
Thx in advance.

---

### Post by iponeverything on 2011-04-18
ssh service is either going controlled through sysV init or upstart.

---

### Post by cryptoboss on 2011-04-18
Ok , but how to force ssh to work only under xinetd??

---

### Post by iponeverything on 2011-04-18
no forcing to it. 

xinetd can't bind to port 22 if it already tied up by sshd.

```
killall -v -9 sshd 
```

will kill your running sshd -- then test out you inetd solution.

sshd will start on the next reboot though 

man upstart

it is the sysV init replacement for service control.

---

### Post by cryptoboss on 2011-04-18
Thanks for your reply , but even when I kill sshd , xinetd wont spawn another sshd :confused:
any idea what could be causing  that??

PS : I'v checked my hosts.deny and  its clean .

---

### Post by iponeverything on 2011-04-18
turn on debugging for xinitd and sshd  -- see which logs are being appended to with "ls -ltr /var/log" then do a tail of correct log to monitor the debug messages.

---

### Post by cryptoboss on 2011-04-18
How can I turn on debugging for xinetd  and sshd ?

---

### Post by iponeverything on 2011-04-21
generally "-d" is for debugging.

Do a "man" the services in question Or just google.

---

