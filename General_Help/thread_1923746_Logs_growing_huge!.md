---
title: "Logs growing huge!"
date: 2012-02-11
forum: General Help
---

### Post by The Phone on 2012-02-11
I have a problem with my ubuntu system logging, these logs are growing big:

kern.log 6.6 gb
messages 6.6 gb
syslog 6.6 gb

I understand that my system has som wrong settings that make the system write unnecessary things.

How do I stop them from continue growing?
How do I delete them correctly? 

I am using Ubuntu 10.10, is there a fix in a later version?


Thanks! ;)

---

### Post by mcduck on 2012-02-11
Well, the way to figure out what's the problem is actually quite simple, take a look inside those log files and see what are the error messages that cause the files to grow that large... ;)

Once you know what the problem is you can start figuring out how to solve it.

---

### Post by Toz on 2012-02-11
> **The Phone said:**
> I have a problem with my ubuntu system logging, these logs are growing big:

kern.log 6.6 gb
messages 6.6 gb
syslog 6.6 gb

I understand that my system has som wrong settings that make the system write unnecessary things.
What unnecessary things are being written? Are those log files being filled with repeated similar messages? If so, what is the message?

> How do I stop them from continue growing?
How do I delete them correctly? 
logrotate should take care of compressing, rotating and backing up the log files. Lets make sure its working correctly. Can you type the following commands into a terminal window and post back the results:
```
ls -l /etc/cron.daily
ls -l /var/lib/logrotate/status
```
...and the contents of the file **/var/lib/logrotate/status**

---

### Post by The Phone on 2012-02-11
> **mcduck said:**
> Well, the way to figure out what's the problem is actually quite simple, take a look inside those log files and see what are the error messages that cause the files to grow that large... ;)

Once you know what the problem is you can start figuring out how to solve it.

Here is a example text in Ufw.log:

```
Feb  5 07:53:11 PhenomX4 kernel: [50204.745923] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=58206 DF PROTO=TCP SPT=60834 DPT=10025 WINDOW=32792 RES=0x00 SYN URGP=0 
Feb  5 07:53:11 PhenomX4 kernel: [50204.745968] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=58206 DF PROTO=TCP SPT=60834 DPT=10025 WINDOW=32792 RES=0x00 SYN URGP=0 
Feb  5 07:53:11 PhenomX4 kernel: [50204.746020] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=10025 DPT=60834 WINDOW=0 RES=0x00 ACK RST URGP=0 
Feb  5 07:53:11 PhenomX4 kernel: [50204.746046] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=10025 DPT=60834 WINDOW=0 RES=0x00 ACK RST URGP=0 
```Here is a example text in messages:

```
Feb  5 07:52:57 PhenomX4 kernel: [50190.742761] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=18522 DF PROTO=TCP SPT=60827 DPT=10025 WINDOW=32792 RES=0x00 SYN URGP=0 
Feb  5 07:52:57 PhenomX4 kernel: [50190.742806] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=18522 DF PROTO=TCP SPT=60827 DPT=10025 WINDOW=32792 RES=0x00 SYN URGP=0 
Feb  5 07:52:57 PhenomX4 kernel: [50190.742858] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=10025 DPT=60827 WINDOW=0 RES=0x00 ACK RST URGP=0 
Feb  5 07:52:57 PhenomX4 kernel: [50190.742884] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=10025 DPT=60827 WINDOW=0 RES=0x00 ACK RST URGP=0 
```
Here is a example text in kern.log

```
Feb  5 07:52:57 PhenomX4 kernel: [50190.742761] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=18522 DF PROTO=TCP SPT=60827 DPT=10025 WINDOW=32792 RES=0x00 SYN URGP=0 
Feb  5 07:52:57 PhenomX4 kernel: [50190.742806] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=18522 DF PROTO=TCP SPT=60827 DPT=10025 WINDOW=32792 RES=0x00 SYN URGP=0 
Feb  5 07:52:57 PhenomX4 kernel: [50190.742858] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=10025 DPT=60827 WINDOW=0 RES=0x00 ACK RST URGP=0 
Feb  5 07:52:57 PhenomX4 kernel: [50190.742884] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=10025 DPT=60827 WINDOW=0 RES=0x00 ACK RST URGP=0 
```
Any suggestions on that this is?

---

### Post by The Phone on 2012-02-11
> **Toz said:**
> What unnecessary things are being written? Are those log files being filled with repeated similar messages? If so, what is the message?


logrotate should take care of compressing, rotating and backing up the log files. Lets make sure its working correctly. Can you type the following commands into a terminal window and post back the results:
```
ls -l /etc/cron.daily
ls -l /var/lib/logrotate/status
```...and the contents of the file **/var/lib/logrotate/status**

Here is the result for the commands:

```
js-admin@PhenomX4:~$ sudo su
[sudo] password for js-admin: 
root@PhenomX4:/home/js-admin# ls -l /etc/cron.daily
totalt 52
-rwxr-xr-x 1 root root   311 2010-06-20 10:11 0anacron
-rwxr-xr-x 1 root root   189 2010-10-01 14:17 apport
-rwxr-xr-x 1 root root 15655 2010-10-05 16:15 apt
-rwxr-xr-x 1 root root   502 2010-05-27 11:28 bsdmainutils
-rwxr-xr-x 1 root root   256 2010-09-08 11:50 dpkg
-rwxr-xr-x 1 root root    89 2010-08-05 23:29 logrotate
-rwxr-xr-x 1 root root  1335 2010-08-17 20:49 man-db
-rwxr-xr-x 1 root root   606 2010-03-24 13:35 mlocate
-rwxr-xr-x 1 root root  2149 2009-06-16 15:12 popularity-contest
-rwxr-xr-x 1 root root  3594 2010-08-24 22:45 standard
root@PhenomX4:/home/js-admin# ls -l /var/lib/logrotate/status
-rw-r--r-- 1 root root 1315 2012-02-11 11:52 /var/lib/logrotate/status
root@PhenomX4:/home/js-admin# 


```


And here is the text inside "status":

```
logrotate state -- version 2
"/var/log/mail.err" 2011-5-28
"/var/log/user.log" 2012-2-5
"/var/log/pm-powersave.log" 2012-2-4
"/var/log/ufw.log" 2012-2-5
"/var/log/jockey.log" 2011-6-17
"/var/log/mail.log" 2011-5-28
"/var/log/lpr.log" 2012-2-5
"/var/log/pm-suspend.log" 2012-2-5
"/var/log/dpkg.log" 2012-2-4
"/var/log/syslog" 2012-2-11
"/var/log/mail.info" 2011-5-28
"/var/log/daemon.log" 2012-2-5
"/var/log/apport.log" 2011-5-28
"/var/log/speech-dispatcher/debug-festival" 2011-5-28
"/var/log/btmp" 2012-2-4
"/var/log/cron.log" 2011-5-28
"/var/log/alternatives.log" 2012-2-4
"/var/log/unattended-upgrades/unattended-upgrades.log" 2011-5-28
"/var/log/cups/access_log" 2012-1-15
"/var/log/mail.warn" 2011-5-28
"/var/log/samba/log.winbindd" 2012-2-11
"/var/log/wtmp" 2012-2-4
"/var/log/clamav/freshclam.log" 2012-2-5
"/var/log/messages" 2012-2-5
"/var/log/speech-dispatcher/debug-epos-generic" 2011-5-28
"/var/log/ConsoleKit/history" 2012-2-4
"/var/log/kern.log" 2012-2-5
"/var/log/apt/term.log" 2012-2-4
"/var/log/auth.log" 2012-2-5
"/var/log/speech-dispatcher/debug-flite" 2011-5-28
"/var/log/ppp-connect-errors" 2011-5-28
"/var/log/apt/history.log" 2012-2-4
"/var/log/debug" 2012-2-5
"/var/log/speech-dispatcher/speech-dispatcher.log" 2011-5-28
"/var/log/speech-dispatcher/speech-dispatcher-protocol.log" 2011-5-28
```

Thanks!

---

### Post by mcduck on 2012-02-11
Have you at any point changed your UFW logging level? Does running "*sudo ufw logging low*" solve the problem? (that should set the logging level to default...)

---

### Post by The Phone on 2012-02-11
> **mcduck said:**
> Have you at any point changed your UFW logging level? Does running "*sudo ufw logging low*" solve the problem? (that should set the logging level to default...)

I had not changed any logging level. But after you suggested the sudo command ```
*ufw logging low*
``` I did change it just now.

How do I delete them safely so I can see if the command helps?

I am not sure how to rotate the log files manually.

---

### Post by Bobhuber on 2012-02-11
> **The Phone said:**
> I had not changed any logging level. But after you suggested the sudo command ```
*ufw logging low*
``` I did change it just now.

How do I delete them safely so I can see if the command helps?

I am not sure how to rotate the log files manually.
You can manually delete any of the log files in /var/log along with the backups (.gz extension files). The log files will be recreated on the next boot. Just leave the directories intact.You will lose any info as to what might be going on but at least it would give you a starting point. I actually store my log files in a tmpfs (ram) and lose them on every boot. Not good if I develop problems but helps with write cycles on my SSD drive.

---

