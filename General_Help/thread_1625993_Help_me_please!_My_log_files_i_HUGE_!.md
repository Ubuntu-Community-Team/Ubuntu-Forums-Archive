---
title: "Help me please! My log files i HUGE !"
date: 2010-11-19
forum: General Help
---

### Post by Lisaac10 on 2010-11-19
Guys how can i delete my log files? They are 131.2 GB! And i need space on my pc :(. And is it ok to delete it ?

---

### Post by WorMzy on 2010-11-19
Yes and no. With log files that humongous, there's probably a good reason for it. Read through the biggest ones, find out what's causing the message spam, fix the problem, ***then*** delete the offending logs.

---

### Post by dcstar on 2010-11-19
> **Lisaac10 said:**
> Guys how can i delete my log files? They are 131.2 GB! And i need space on my pc :(. And is it ok to delete it ?

If log files are that large then you have a problem with your system that is filling them - look at them and find the root cause of the problem.

You can delete the log files using **logrotate**, but that is only ignoring the symptoms of an obvious underlying problem.

---

### Post by Lisaac10 on 2010-11-19
> **WorMzy said:**
> Yes and no. With log files that humongous, there's probably a good reason for it. Read through the biggest ones, find out what's causing the message spam, fix the problem, ***then*** delete the offending logs.

Thanks Guys ! Ill check it out in a minute. But, do you guys have any advise for me ? Im kinda new to linux

---

### Post by WorMzy on 2010-11-19
Without seeing the logs, there's not much me we can give you in the way of advice, I'm afraid. Take a look, post the most repeated messages, and we'll see what we can suggest.

---

### Post by Lisaac10 on 2010-11-20
> **WorMzy said:**
> Without seeing the logs, there's not much me we can give you in the way of advice, I'm afraid. Take a look, post the most repeated messages, and we'll see what we can suggest.
These type of messages keep repeating itself!

 1492.093536] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=308 
Nov 20 11:12:28 isaac-desktop kernel: [ 1493.335184] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=308 
Nov 20 11:12:29 isaac-desktop kernel: [ 1493.786197] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=384 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=364 
Nov 20 11:12:32 isaac-desktop kernel: [ 1496.741354] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=384 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=364 
Nov 20 11:12:32 isaac-desktop kernel: [ 1497.145092] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=308 
Nov 20 11:12:36 isaac-desktop kernel: [ 1501.481010] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=308 
Nov 20 11:12:38 isaac-desktop kernel: [ 1502.801938] [UFW AUDIT] IN=eth0 OUT= MAC=00:1a:a0:9a:f2:28:00:01:5c:32:cd:01:08:00 SRC=91.189.94.12 DST=69.86.246.68 LEN=52 TOS=0x00 PREC=0x00 TTL=50 ID=58106 DF PROTO=TCP SPT=80 DPT=58525 WINDOW=60 RES=0x00 ACK FIN URGP=0 
Nov 20 11:12:38 isaac-desktop kernel: [ 1502.840037] [UFW AUDIT] IN= OUT=eth0 SRC=69.86.246.68 DST=91.189.94.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=61252 DF PROTO=TCP SPT=58525 DPT=80 WINDOW=1002 RES=0x00 ACK URGP=0 
Nov 20 11:12:39 isaac-desktop kernel: [ 1503.712077] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=384 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=364 
Nov 20 11:12:39 isaac-desktop kernel: [ 1504.468315] [UFW AUDIT] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Nov 20 11:12:41 isaac-desktop kernel: [ 1506.200921] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=384 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=364 
Nov 20 11:12:41 isaac-desktop kernel: [ 1506.490100] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=308 
Nov 20 11:12:42 isaac-desktop kernel: [ 1506.769399] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=308 
Nov 20 11:12:43 isaac-desktop kernel: [ 1507.889191] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=308 
Nov 20 11:12:44 isaac-desktop kernel: [ 1509.164771] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=384 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=364 
Nov 20 11:12:46 isaac-desktop kernel: [ 1510.575686] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=384 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=364 
Nov 20 11:12:46 isaac-desktop kernel: [ 1510.580128] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=384 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=364 
Nov 20 11:12:46 isaac-desktop kernel: [ 1510.584864] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=384 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=364 
Nov 20 11:12:46 isaac-desktop kernel: [ 1510.592109] [UFW AUDIT] IN= OUT=eth0 SRC=69.86.246.68 DST=91.189.94.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=61253 DF PROTO=TCP SPT=58525 DPT=80 WINDOW=1002 RES=0x00 ACK FIN URGP=0 
Nov 20 11:12:46 isaac-desktop kernel: [ 1510.678598] [UFW AUDIT] IN=eth0 OUT= MAC=00:1a:a0:9a:f2:28:00:01:5c:32:cd:01:08:00 SRC=91.189.94.12 DST=69.86.246.68 LEN=52 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=TCP SPT=80 DPT=58525 WINDOW=60 RES=0x00 ACK URGP=0 
Nov 20 11:12:46 isaac-desktop kernel: [ 1511.146066] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=308 
Nov 20 11:12:47 isaac-desktop kernel: [ 1511.699225] [UFW AUDIT] IN= OUT=eth0 SRC=69.86.246.68 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Nov 20 11:12:47 isaac-desktop kernel: [ 1511.699238] [UFW ALLOW] IN= OUT=eth0 SRC=69.86.246.68 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Nov 20 11:12:47 isaac-desktop kernel: [ 1511.699274] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=69.86.246.68 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Nov 20 11:12:47 isaac-desktop kernel: [ 1511.964705] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=308 
Nov 20 11:12:49 isaac-desktop kernel: [ 1513.952893] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=308 
Nov 20 11:12:51 isaac-desktop kernel: [ 1515.869209] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=308 
Nov 20 11:12:51 isaac-desktop kernel: [ 1516.368832] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=308 
Nov 20 11:12:52 isaac-desktop kernel: [ 1517.380574] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=308 
Nov 20 11:12:52 isaac-desktop kernel: [ 1517.391027] [UFW AUDIT] IN=eth0 OUT= MAC=00:1a:a0:9a:f2:28:00:01:5c:32:cd:01:08:00 SRC=173.71.154.150 DST=69.86.246.68 LEN=63 TOS=0x00 PREC=0x00 TTL=112 ID=21924 PROTO=UDP SPT=5226 DPT=15332 LEN=43 
Nov 20 11:12:52 isaac-desktop kernel: [ 1517.391066] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:9a:f2:28:00:01:5c:32:cd:01:08:00 SRC=173.71.154.150 DST=69.86.246.68 LEN=63 TOS=0x00 PREC=0x00 TTL=112 ID=21924 PROTO=UDP SPT=5226 DPT=15332 LEN=43 
Nov 20 11:12:54 isaac-desktop kernel: [ 1518.722600] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=384 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=364 
Nov 20 11:12:55 isaac-desktop kernel: [ 1519.791325] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=308 
Nov 20 11:12:56 isaac-desktop kernel: [ 1521.479599] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=308 
Nov 20 11:12:59 isaac-desktop kernel: [ 1524.494054] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:32:cd:01:08:00 SRC=10.85.0.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=308

---

### Post by WorMzy on 2010-11-20
Seems to be similar to this bug: [https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/591181](https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/591181)

Try following some of the suggestions in the comments, the original reporter seems to have fixed it on his machine, so it must be possible for you to do so yourself.

---

