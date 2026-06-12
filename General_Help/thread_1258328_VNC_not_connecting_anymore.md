---
title: "VNC not connecting anymore?"
date: 2009-09-04
forum: General Help
---

### Post by Juihi on 2009-09-04
Hey guy's, a couple of days ago I suddenly had VNC close down on me and each time I try to connect to it, it just says "Connection closed", so I thought I would kill the process in Putty, so I type in "vncserver -kill :1"  and it comes up with this message

> Can't find file /root/.vnc/hosted-by:1.pid
You'll have to kill the Xtightvnc process manuallyI have absolutely no idea what to do next and I'm quite stumped as to why it's done this, admittedly I was to get utorrent to pop up (I'm very new to Linux) and clicked something called "icons" which closed it down, any help would be greatly appreciated.

---

### Post by XCan on 2009-09-05
```
 ps aux | grep xtightvnc 
``` 

the kill whatever pid it returns and restart it. :)

---

### Post by Juihi on 2009-09-05
I typed in that command and it came up with some random number lol, but how do I kill the .pid ?

---

### Post by Petertje on 2009-09-05
execute
```

kill <number you found>

```or you can use:
system->control->systemmonitor
to list all your running processes and select and kill the one you need:)

but VNC doesn't just close connections at random intervals, atleast it should not. Does it have any logs? Cause by restarting it you're fighting the symptom(s), not the cause.

---

### Post by Juihi on 2009-09-05
I'm not sure if VNC has logs? how would I find out?

And I tried kill command on the number it displayed but it says "No such process" :confused:

---

### Post by Petertje on 2009-09-06
have you tried the systemmonitor and finding the vnc process and killing it?
for log files check this folder:
```

/var/log/

```

---

### Post by Juihi on 2009-09-06
I type that in and it just says it's a directory? 

(I should mention that Linux is on a seedbox I own and I was accessing it via VNC, I can still log onto it via putty though)

---

### Post by XCan on 2009-09-06
Post the output of 
```
 ps aux | grep xtightvnc 
```

and post the output of ```
 ls -l /var/log 
```

---

### Post by Lucky75 on 2009-09-06
you may need to do a:

```
kill -9 <PID # you found>
``` or 
```
sudo kill -9 <PID # you found>
```

---

### Post by The Cog on 2009-09-06
The command **killall xtightvnc** should do the trick. Saves messing with pid numbers.

---

### Post by Juihi on 2009-09-07
I tired that killall command but I just get "xtightvnc: no process killed"

but I run these commands

> $ chmod +x .vnc/xstartup
$ vncserver :1

Warning: *****:1 is taken because of /tmp/.X1-lock
Remove this file if there is no X server hosted-by:1
A VNC server is already running as :1
So there obviously is a VNC server running but I just can't kill it :(



> **XCan said:**
> Post the output of
```
 ps aux | grep xtightvnc 
```and post the output of ```
 ls -l /var/log 
```

# ps aux | grep xtightvnc
root     19725  0.0  0.0   2292   716 pts/0    S+   11:16   0:00 grep xtightvnc
root@hosted-by:~# ls -l /var/log


t   adm     4096 2009-09-07 06:51 apache2
drwxr-xr-x 2 root   root    4096 2009-05-06 12:59 apparmor
drwxr-xr-x 2 root   root    4096 2009-09-01 06:58 apt
-rw-r----- 1 syslog adm    85546 2009-09-07 11:15 auth.log
-rw-r----- 1 syslog adm   497433 2009-09-06 06:47 auth.log.0
-rw-r----- 1 syslog adm    34436 2009-08-30 06:47 auth.log.1.gz
-rw-r----- 1 syslog adm    14359 2009-08-23 06:47 auth.log.2.gz
-rw-r----- 1 root   adm       31 2009-08-21 13:11 boot
-rw-rw---- 1 root   utmp       0 2009-09-01 06:58 btmp
-rw-rw-r-- 1 root   utmp       0 2009-08-21 13:11 btmp.1
drwxr-xr-x 2 root   root    4096 2009-08-23 09:14 ConsoleKit
-rw-r----- 1 syslog adm        0 2009-08-30 06:48 daemon.log
-rw-r----- 1 syslog adm     1560 2009-08-23 09:14 daemon.log.0
-rw-r----- 1 syslog adm     1042 2009-08-22 01:31 daemon.log.1.gz
-rw-r----- 1 syslog adm        0 2009-09-06 06:47 debug
-rw-r----- 1 syslog adm    12015 2009-09-02 23:36 debug.0
-rw-r----- 1 syslog adm      413 2009-08-29 08:47 debug.1.gz
-rw-r----- 1 syslog adm     1935 2009-08-22 01:32 debug.2.gz
drwxr-xr-x 2 root   root    4096 2008-11-04 20:04 dist-upgrade
-rw-r----- 1 root   adm    32618 2009-08-21 13:19 dmesg
-rw-r----- 1 root   adm       31 2009-08-21 13:11 dmesg.0
-rw-r----- 1 root   adm        0 2009-09-01 06:58 dpkg.log
-rw-r----- 1 root   adm   420007 2009-08-24 11:25 dpkg.log.1
-rw-r--r-- 1 root   root   24024 2009-08-23 09:14 faillog
-rw-r--r-- 1 root   root     924 2009-08-24 10:35 fontconfig.log
drwxr-xr-x 2 root   root    4096 2009-08-21 13:11 fsck
drwxr-xr-x 3 root   root    4096 2009-08-21 13:17 installer
-rw-r----- 1 syslog adm    82673 2009-09-07 11:13 kern.log
-rw-r----- 1 syslog adm  1077898 2009-09-06 06:39 kern.log.0
-rw-r----- 1 syslog adm    84317 2009-09-01 06:58 kern.log.1.gz
-rw-r----- 1 syslog adm    33957 2009-08-30 06:43 kern.log.2.gz
-rw-r----- 1 syslog adm    98724 2009-08-29 06:58 kern.log.3.gz
-rw-rw-r-- 1 root   utmp  292292 2009-09-07 10:45 lastlog
-rw-r----- 1 syslog adm        0 2009-08-21 13:11 lpr.log
-rw-r----- 1 syslog adm        0 2009-08-21 13:11 mail.err
-rw-r----- 1 syslog adm        0 2009-08-21 13:11 mail.info
-rw-r----- 1 syslog adm        0 2009-08-21 13:11 mail.log
-rw-r----- 1 syslog adm        0 2009-08-21 13:11 mail.warn
-rw-r----- 1 syslog adm    83960 2009-09-07 11:13 messages
-rw-r----- 1 syslog adm  1066995 2009-09-06 06:39 messages.0
-rw-r----- 1 syslog adm    84297 2009-09-01 06:58 messages.1.gz
-rw-r----- 1 syslog adm    33881 2009-08-30 06:43 messages.2.gz
-rw-r----- 1 syslog adm    99387 2009-08-29 06:58 messages.3.gz
drwxr-s--- 2 mysql  adm     4096 2009-08-21 13:15 mysql
-rw-r----- 1 mysql  adm        0 2009-08-21 13:15 mysql.err
-rw-r----- 1 mysql  adm        0 2009-09-07 06:51 mysql.log
-rw-r----- 1 mysql  adm       20 2009-09-06 07:14 mysql.log.1.gz
-rw-r----- 1 mysql  adm       20 2009-09-05 07:18 mysql.log.2.gz
-rw-r----- 1 mysql  adm       20 2009-09-04 06:33 mysql.log.3.gz
-rw-r----- 1 mysql  adm       20 2009-09-03 06:43 mysql.log.4.gz
-rw-r----- 1 mysql  adm       20 2009-09-02 07:14 mysql.log.5.gz
-rw-r----- 1 mysql  adm       20 2009-09-01 06:58 mysql.log.6.gz
-rw-r----- 1 mysql  adm       20 2009-08-31 06:32 mysql.log.7.gz
drwxr-sr-x 2 news   news    4096 2009-08-21 13:19 news
-rw-r--r-- 1 root   root       0 2009-08-21 13:15 pycentral.log
drwxr-x--- 3 root   adm     4096 2009-08-30 06:34 samba
-rw-r--r-- 1 root   root       0 2009-09-06 07:14 scrollkeeper.log
-rw-r--r-- 1 root   root     641 2009-09-01 06:52 scrollkeeper.log.1
-rw-r--r-- 1 root   root     662 2009-08-24 11:25 scrollkeeper.log.2
-rw-r----- 1 syslog adm    17431 2009-09-07 11:15 syslog
-rw-r----- 1 syslog adm   134268 2009-09-07 06:50 syslog.0
-rw-r----- 1 syslog adm    10829 2009-09-06 07:10 syslog.1.gz
-rw-r----- 1 syslog adm    15531 2009-09-05 07:17 syslog.2.gz
-rw-r----- 1 syslog adm    23054 2009-09-04 06:31 syslog.3.gz
-rw-r----- 1 syslog adm    25141 2009-09-03 06:40 syslog.4.gz
-rw-r----- 1 syslog adm    32839 2009-09-02 07:13 syslog.5.gz
-rw-r----- 1 syslog adm    52204 2009-09-01 06:58 syslog.6.gz
-rw-r--r-- 1 root   root  339141 2009-08-21 13:18 udev
drwxr-xr-x 2 root   root    4096 2008-10-13 13:52 unattended-upgrades
-rw-r----- 1 syslog adm        0 2009-08-21 13:11 user.log
-rw-rw-r-- 1 root   utmp   14592 2009-09-07 10:45 wtmp
-rw-rw-r-- 1 root   utmp   23808 2009-08-31 21:40 wtmp.1



> **Lucky75 said:**
> you may need to do a:

```
kill -9 <PID # you found>
``` or 
```
sudo kill -9 <PID # you found>
```

I just get > [B]-bash: kill: hosted-by:1.pid: arguments must be process or job IDs
[/B]

---

### Post by XCan on 2009-09-07
Hmm, it seems like your vnc process isn't called xtightvnc, try then ```
 ps aux | grep vnc 
```

---

### Post by Juihi on 2009-09-07
This is what I get when I type in that command

> root     22955  0.0  0.0   2292   716 pts/0    S+   21:56   0:00 grep vnc


---

### Post by XCan on 2009-09-07
That's peculiar, do you have any idea at all what your xtightvnc process is called? Or perhaps it's not even running atm?

---

### Post by Juihi on 2009-09-08
I believe there is a VNC server still running, I used this guide [http://filesharingtalk.com/vb3/f-guides-and-tutorials-65/t-naqs-complete-setup-guide-linux-seedboxes-fedora-corecentosdebianubuntu-281331](http://filesharingtalk.com/vb3/f-guides-and-tutorials-65/t-naqs-complete-setup-guide-linux-seedboxes-fedora-corecentosdebianubuntu-281331) **Step 5** to setup VNC

---

### Post by Juihi on 2009-09-11
Righto, I have a bigger problem now, I can't even connect to my seedbox! I just get a connection time out message when I connect with Putty, I typed this command "iptables -F" in, and then it hasn't let me connect anymore, I have 2 IP's plus a gateway IP, I don't get any responses from the 2 IP's but I do get one from the gateway, this keeps on getting worse and worse :confused::confused::(


Edit

I contacted the support from Leaseweb (where I got the seedbox from) and they have fixed the above problem for me, in quite a sort space of time I might add! very happy :)

---

### Post by Juihi on 2009-09-19
Hey guys, me again with the same problem :confused:  I had it all up and running perfectly, I mearly right clicked on the desktop bit in VNC to bring up the drop down box thingy and it just closed VNC and now won't let me connect again with the same message as before "Connection closed."   I am able to still log in fine via Putty which is good & I can connect via Filezillla as well, but this seems like exactly the same problem as I had before, I've tried killing the vncserver as before but once again had the same problems as before.

---

### Post by Juihi on 2009-09-20
I contacted the techincal support again, unfortunately tightvnc isn't covered under their free service and it would going to cost and fortune for them to help out, but they mentioned they couldn't  ping, SSH or portscan the server which was odd given I was connected to it via Putty and also downloading a file from it via Filezilla and I was able to ping it, just bloody VNC isn't working

---

### Post by athenaa on 2010-07-26
Hi everyone,

I have almost the same question.

I try to connect to my ubuntu machine from a windows, but I just get a black screen and mouse pointer. the machine is connected, but I can't see anything on the screen.

I looked on the internet, but I still don't know what to do.
I'm desperate!  :(

Thanks for your help,

---

