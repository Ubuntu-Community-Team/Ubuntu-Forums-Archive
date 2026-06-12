---
title: "unwanted HDD activity caused by cronjob"
date: 2011-02-09
forum: General Help
---

### Post by cyvi on 2011-02-09
I'm getting unwanted HDD activity in the middle of the night that takes about two hours. And this happens every night. I can pinpoint the starting time to 02:00 in the morning. The HDD is reading about 2MB/s thus making noise that makes it difficult for me to sleep.

By examining auth.log log I managed to find the following:

Feb 10 02:00:01 xxx CRON[25162]: pam_unix(cron:session): session opened for user root by (uid=0)
...
Feb 10 04:18:16 xxx CRON[25162]: pam_unix(cron:session): session closed for user root

I'm running Ubuntu 10.10.

After quite a bit of searching I couldn't find a similar problem. Didn't find the cron documentation helpful, either.

---

### Post by Cheesehead on 2011-02-10
Please post the results of the following five commands:```

cat /var/log/syslog | grep cron
cat /etc/crontab
cat /etc/anacrontab 
ls /etc | grep cron
ls /etc/cron.daily

```

Is your system awake *all* night? Or is it asleep/shutdown part of the time?
Does the activity occur at exactly 2:00 every night? Or does it wander a bit?

Linux does need to do some daily activities to stay healthy. *If* these daily cronjobs are responsible for the activity, it should be trivial to reschedule them.

---

### Post by cyvi on 2011-02-10
> **Cheesehead said:**
> Please post the results of the following five commands:```

cat /var/log/syslog | grep cron
cat /etc/crontab
cat /etc/anacrontab 
ls /etc | grep cron
ls /etc/cron.daily

```

Is your system awake *all* night? Or is it asleep/shutdown part of the time?
Does the activity occur at exactly 2:00 every night? Or does it wander a bit?

Linux does need to do some daily activities to stay healthy. *If* these daily cronjobs are responsible for the activity, it should be trivial to reschedule them.

First of all I'd like to thank you for your reply. 

Either the system is powered off or totally awake. When I noticed the activity I checked the time and the auth.log for activity and I noticed the above cronjob and around 4:20AM I noticed that the activity stopped. I've only managed to pin point the beginning of this activity once, other times I haven't paid that much attention to exact times.

Here is the output for the commands you asked.
```
rgms@kurkobuntu:~$ cat /var/log/syslog | grep cron
Feb 10 07:40:46 kurkobuntu anacron[801]: Job `cron.daily' terminated
Feb 10 07:40:46 kurkobuntu anacron[801]: Normal exit (1 job run)
Feb 10 08:00:01 kurkobuntu CRON[16673]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Feb 10 08:00:03 kurkobuntu /usr/bin/crontab[17871]: (root) LIST (nobody)
Feb 10 08:17:01 kurkobuntu CRON[19062]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 10 09:00:01 kurkobuntu CRON[19367]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Feb 10 09:17:01 kurkobuntu CRON[19619]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 10 10:00:01 kurkobuntu CRON[19958]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Feb 10 10:17:01 kurkobuntu CRON[20464]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 10 11:00:01 kurkobuntu CRON[20806]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Feb 10 11:17:01 kurkobuntu CRON[21069]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 10 12:00:01 kurkobuntu CRON[21404]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Feb 10 12:17:01 kurkobuntu CRON[21672]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 10 13:00:01 kurkobuntu CRON[22036]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Feb 10 13:17:01 kurkobuntu CRON[22277]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 10 14:00:02 kurkobuntu CRON[31753]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Feb 10 14:17:02 kurkobuntu CRON[32444]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 10 15:00:01 kurkobuntu CRON[917]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Feb 10 15:17:01 kurkobuntu CRON[1424]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 10 15:50:21 kurkobuntu cron[1353]: (CRON) INFO (pidfile fd = 3)
Feb 10 15:50:21 kurkobuntu anacron[1363]: Anacron 2.3 started on 2011-02-10
Feb 10 15:50:21 kurkobuntu cron[1369]: (CRON) STARTUP (fork ok)
Feb 10 15:50:21 kurkobuntu cron[1369]: (CRON) INFO (Running @reboot jobs)
Feb 10 15:50:21 kurkobuntu anacron[1363]: Normal exit (0 jobs run)
Feb 10 15:50:30 kurkobuntu anacron[1728]: Anacron 2.3 started on 2011-02-10
Feb 10 15:50:30 kurkobuntu anacron[1728]: Normal exit (0 jobs run)
Feb 10 16:00:01 kurkobuntu CRON[2890]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Feb 10 16:00:03 kurkobuntu /usr/bin/crontab[4078]: (root) LIST (nobody)
Feb 10 16:17:02 kurkobuntu CRON[5281]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 10 17:00:01 kurkobuntu CRON[5736]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Feb 10 17:17:01 kurkobuntu CRON[5913]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 10 18:00:01 kurkobuntu CRON[6090]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Feb 10 18:17:01 kurkobuntu CRON[6497]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 10 19:00:01 kurkobuntu CRON[7466]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Feb 10 19:17:01 kurkobuntu CRON[7872]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 10 20:00:01 kurkobuntu CRON[8058]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Feb 10 20:17:01 kurkobuntu CRON[8629]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
rgms@kurkobuntu:~$ cat /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#


rgms@kurkobuntu:~$ cat /etc/anacrontab
# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1	5	cron.daily	 nice run-parts --report /etc/cron.daily
7	10	cron.weekly	 nice run-parts --report /etc/cron.weekly
@monthly	15	cron.monthly nice run-parts --report /etc/cron.monthly

rgms@kurkobuntu:~$ ls /etc | grep cron
anacrontab
cron.d
cron.daily
cron.hourly
cron.monthly
crontab
cron.weekly
rgms@kurkobuntu:~$ ls /etc/cron.daily
0anacron  aptitude           dpkg       ntp
acct      apt-show-versions  logrotate  popularity-contest
apport    bsdmainutils       man-db     rkhunter
apt       chkrootkit         mlocate    standard

```

---

### Post by Cheesehead on 2011-02-10
So far everything looks normal. Quite ordinary, I see nothing unusual at all...

I neglected to ask for the output of 'cat /var/log/syslog.1 | grep cron' (covers the overnight hours before your logs get rotated in the morning).
Please post it, and let's see what's happening at night...

---

### Post by cyvi on 2011-02-11
```
Feb 11 01:59:35 kurkobuntu ntpd[2530]: kernel time sync status change 6001
Feb 11 02:00:01 kurkobuntu CRON[5150]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Feb 11 02:03:29 kurkobuntu kernel: [36806.510479] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=124.160.133.160 DST=109.108.2.251 LEN=133 TOS=0x00 PREC=0x00 TTL=35 ID=58397 PROTO=UDP SPT=4032 DPT=56260 LEN=113 
Feb 11 02:06:09 kurkobuntu kernel: [36967.156334] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=69.63.181.105 DST=109.108.2.251 LEN=182 TOS=0x00 PREC=0x00 TTL=80 ID=33469 DF PROTO=TCP SPT=5222 DPT=60361 WINDOW=91 RES=0x00 ACK PSH URGP=0 
Feb 11 02:06:36 kurkobuntu kernel: [36993.331525] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=69.63.181.105 DST=109.108.2.251 LEN=182 TOS=0x00 PREC=0x00 TTL=80 ID=33470 DF PROTO=TCP SPT=5222 DPT=60361 WINDOW=91 RES=0x00 ACK PSH URGP=0 
Feb 11 02:07:28 kurkobuntu kernel: [37045.683396] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=69.63.181.105 DST=109.108.2.251 LEN=182 TOS=0x00 PREC=0x00 TTL=80 ID=33471 DF PROTO=TCP SPT=5222 DPT=60361 WINDOW=91 RES=0x00 ACK PSH URGP=0 
Feb 11 02:09:13 kurkobuntu kernel: [37150.384861] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=69.63.181.105 DST=109.108.2.251 LEN=182 TOS=0x00 PREC=0x00 TTL=80 ID=33472 DF PROTO=TCP SPT=5222 DPT=60361 WINDOW=91 RES=0x00 ACK PSH URGP=0 
Feb 11 02:09:48 kurkobuntu kernel: [37186.069412] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=219.108.152.105 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=102 ID=9109 DF PROTO=TCP SPT=60299 DPT=58911 WINDOW=8192 RES=0x00 ACK SYN URGP=0 
Feb 11 02:09:51 kurkobuntu kernel: [37189.073723] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=219.108.152.105 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=102 ID=9375 DF PROTO=TCP SPT=60302 DPT=58911 WINDOW=8192 RES=0x00 ACK SYN URGP=0 
Feb 11 02:09:57 kurkobuntu kernel: [37195.083411] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=219.108.152.105 DST=109.108.2.251 LEN=56 TOS=0x00 PREC=0x00 TTL=102 ID=10511 DF PROTO=TCP SPT=60312 DPT=58911 WINDOW=8192 RES=0x00 ACK SYN URGP=0 
Feb 11 02:10:00 kurkobuntu kernel: [37197.508593] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=173.24.137.238 DST=109.108.2.251 LEN=1500 TOS=0x00 PREC=0x00 TTL=105 ID=18253 DF PROTO=TCP SPT=57238 DPT=60060 WINDOW=63491 RES=0x00 ACK PSH URGP=0 
Feb 11 02:10:30 kurkobuntu kernel: [37228.026779] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=173.24.137.238 DST=109.108.2.251 LEN=1500 TOS=0x00 PREC=0x00 TTL=105 ID=31663 DF PROTO=TCP SPT=57238 DPT=60060 WINDOW=63287 RES=0x00 ACK PSH URGP=0 
Feb 11 02:10:58 kurkobuntu kernel: [37255.819195] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=173.24.137.238 DST=109.108.2.251 LEN=1500 TOS=0x00 PREC=0x00 TTL=105 ID=10597 DF PROTO=TCP SPT=57238 DPT=60060 WINDOW=63134 RES=0x00 ACK PSH URGP=0 
Feb 11 02:11:00 kurkobuntu kernel: [37257.280953] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=173.24.137.238 DST=109.108.2.251 LEN=1500 TOS=0x00 PREC=0x00 TTL=105 ID=11054 DF PROTO=TCP SPT=57238 DPT=60060 WINDOW=63134 RES=0x00 ACK PSH URGP=0 
Feb 11 02:11:08 kurkobuntu kernel: [37265.297045] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=173.24.137.238 DST=109.108.2.251 LEN=1500 TOS=0x00 PREC=0x00 TTL=105 ID=14141 DF PROTO=TCP SPT=57238 DPT=60060 WINDOW=63134 RES=0x00 ACK PSH URGP=0 
Feb 11 02:11:13 kurkobuntu kernel: [37270.382840] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=69.63.181.105 DST=109.108.2.251 LEN=182 TOS=0x00 PREC=0x00 TTL=80 ID=33473 DF PROTO=TCP SPT=5222 DPT=60361 WINDOW=91 RES=0x00 ACK PSH URGP=0 
Feb 11 02:11:19 kurkobuntu kernel: [37276.425413] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=173.24.137.238 DST=109.108.2.251 LEN=1500 TOS=0x00 PREC=0x00 TTL=105 ID=18420 DF PROTO=TCP SPT=57238 DPT=60060 WINDOW=63134 RES=0x00 ACK PSH URGP=0 
Feb 11 02:11:47 kurkobuntu kernel: [37305.007446] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=173.24.137.238 DST=109.108.2.251 LEN=208 TOS=0x00 PREC=0x00 TTL=107 ID=30617 DF PROTO=TCP SPT=22574 DPT=59592 WINDOW=260 RES=0x00 ACK PSH URGP=0 
Feb 11 02:13:13 kurkobuntu kernel: [37390.380894] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=69.63.181.105 DST=109.108.2.251 LEN=182 TOS=0x00 PREC=0x00 TTL=80 ID=33474 DF PROTO=TCP SPT=5222 DPT=60361 WINDOW=91 RES=0x00 ACK PSH URGP=0 
Feb 11 02:14:18 kurkobuntu kernel: [37455.350505] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=173.24.137.238 DST=109.108.2.251 LEN=1500 TOS=0x00 PREC=0x00 TTL=107 ID=24421 DF PROTO=TCP SPT=22574 DPT=59592 WINDOW=256 RES=0x00 ACK URGP=0 
Feb 11 02:14:18 kurkobuntu kernel: [37455.632580] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=173.24.137.238 DST=109.108.2.251 LEN=1500 TOS=0x00 PREC=0x00 TTL=107 ID=24540 DF PROTO=TCP SPT=22574 DPT=59592 WINDOW=256 RES=0x00 ACK URGP=0 
Feb 11 02:14:26 kurkobuntu kernel: [37464.034280] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=173.24.137.238 DST=109.108.2.251 LEN=1500 TOS=0x00 PREC=0x00 TTL=107 ID=27939 DF PROTO=TCP SPT=22574 DPT=59592 WINDOW=255 RES=0x00 ACK URGP=0 
Feb 11 02:14:27 kurkobuntu kernel: [37464.432368] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=173.24.137.238 DST=109.108.2.251 LEN=1500 TOS=0x00 PREC=0x00 TTL=107 ID=28079 DF PROTO=TCP SPT=22574 DPT=59592 WINDOW=255 RES=0x00 ACK URGP=0 
Feb 11 02:15:13 kurkobuntu kernel: [37510.378900] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=69.63.181.105 DST=109.108.2.251 LEN=182 TOS=0x00 PREC=0x00 TTL=80 ID=33475 DF PROTO=TCP SPT=5222 DPT=60361 WINDOW=91 RES=0x00 ACK PSH URGP=0 
Feb 11 02:16:41 kurkobuntu ntpd[2530]: kernel time sync status change 2001
Feb 11 02:17:01 kurkobuntu CRON[5681]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 11 02:17:04 kurkobuntu kernel: [37621.289459] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=108.77.56.56 DST=109.108.2.251 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=4862 DF PROTO=TCP SPT=2947 DPT=36160 WINDOW=65535 RES=0x00 SYN URGP=0 
Feb 11 02:17:04 kurkobuntu kernel: [37621.290771] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=108.77.56.56 DST=109.108.2.251 LEN=47 TOS=0x00 PREC=0x00 TTL=109 ID=4865 PROTO=UDP SPT=41380 DPT=36160 LEN=27 
Feb 11 02:17:07 kurkobuntu kernel: [37624.298185] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=108.77.56.56 DST=109.108.2.251 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=4870 DF PROTO=TCP SPT=2947 DPT=36160 WINDOW=65535 RES=0x00 SYN URGP=0 
Feb 11 02:17:13 kurkobuntu kernel: [37630.233053] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=108.77.56.56 DST=109.108.2.251 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=4871 DF PROTO=TCP SPT=2947 DPT=36160 WINDOW=65535 RES=0x00 SYN URGP=0 
Feb 11 02:17:13 kurkobuntu kernel: [37630.376648] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=69.63.181.105 DST=109.108.2.251 LEN=182 TOS=0x00 PREC=0x00 TTL=80 ID=33476 DF PROTO=TCP SPT=5222 DPT=60361 WINDOW=91 RES=0x00 ACK PSH URGP=0 
Feb 11 02:18:30 kurkobuntu kernel: [37707.874485] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=130 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=110 
Feb 11 02:18:32 kurkobuntu kernel: [37709.828711] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=130 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=110 
Feb 11 02:18:36 kurkobuntu kernel: [37713.830744] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=130 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=110 
Feb 11 02:19:13 kurkobuntu kernel: [37750.374712] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=69.63.181.105 DST=109.108.2.251 LEN=182 TOS=0x00 PREC=0x00 TTL=80 ID=33477 DF PROTO=TCP SPT=5222 DPT=60361 WINDOW=91 RES=0x00 ACK PSH URGP=0 
Feb 11 02:21:13 kurkobuntu kernel: [37870.374911] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=69.63.181.105 DST=109.108.2.251 LEN=182 TOS=0x00 PREC=0x00 TTL=80 ID=33478 DF PROTO=TCP SPT=5222 DPT=60361 WINDOW=91 RES=0x00 ACK PSH URGP=0 
Feb 11 02:29:28 kurkobuntu kernel: [38365.547367] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=71.115.55.230 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=42 ID=34357 DF PROTO=TCP SPT=50822 DPT=39573 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 02:29:28 kurkobuntu kernel: [38366.052570] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=71.115.55.230 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=44 ID=59461 DF PROTO=TCP SPT=50830 DPT=39573 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 02:33:01 kurkobuntu kernel: [38578.832110] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=147.46.15.166 DST=109.108.2.251 LEN=48 TOS=0x00 PREC=0x00 TTL=99 ID=4750 PROTO=TCP SPT=33055 DPT=22 WINDOW=65535 RES=0x00 SYN URGP=0 
Feb 11 02:33:28 kurkobuntu kernel: [38605.570038] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=71.115.55.230 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=44 ID=37541 DF PROTO=TCP SPT=50121 DPT=39573 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 02:33:28 kurkobuntu kernel: [38606.072230] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=71.115.55.230 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=44 ID=62377 DF PROTO=TCP SPT=50124 DPT=39573 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 02:35:12 kurkobuntu dhclient: DHCPREQUEST of 109.108.2.251 on eth0 to 213.243.153.175 port 67
Feb 11 02:35:12 kurkobuntu dhclient: DHCPACK of 109.108.2.251 from 213.243.153.175
Feb 11 02:35:12 kurkobuntu dhclient: bound to 109.108.2.251 -- renewal in 8638 seconds.
Feb 11 02:39:36 kurkobuntu kernel: [38973.541049] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=64.56.157.135 DST=109.108.2.251 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=13529 DF PROTO=TCP SPT=3657 DPT=21 WINDOW=16384 RES=0x00 SYN URGP=0 
Feb 11 02:39:39 kurkobuntu kernel: [38976.501028] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=64.56.157.135 DST=109.108.2.251 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=14397 DF PROTO=TCP SPT=3657 DPT=21 WINDOW=16384 RES=0x00 SYN URGP=0 
Feb 11 02:48:26 kurkobuntu kernel: [39504.126219] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 02:48:28 kurkobuntu kernel: [39506.146805] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 02:48:32 kurkobuntu kernel: [39510.175478] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 02:50:50 kurkobuntu ntpd[2530]: kernel time sync status change 6001
Feb 11 03:00:01 kurkobuntu CRON[5768]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Feb 11 03:03:28 kurkobuntu kernel: [40405.777306] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=71.115.55.230 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=45 ID=62181 DF PROTO=TCP SPT=50671 DPT=39573 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 03:03:29 kurkobuntu kernel: [40406.276210] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=71.115.55.230 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=44 ID=55999 DF PROTO=TCP SPT=50673 DPT=39573 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 03:17:02 kurkobuntu CRON[5918]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 11 03:18:22 kurkobuntu kernel: [41299.764917] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.145.225.22 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=57 ID=47797 DF PROTO=TCP SPT=46909 DPT=53290 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 11 03:18:25 kurkobuntu kernel: [41302.767437] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.145.225.22 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=57 ID=47798 DF PROTO=TCP SPT=46909 DPT=53290 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 11 03:18:28 kurkobuntu kernel: [41305.909690] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 03:18:30 kurkobuntu kernel: [41307.935705] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 03:18:31 kurkobuntu kernel: [41308.755735] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.145.225.22 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=57 ID=47799 DF PROTO=TCP SPT=46909 DPT=53290 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 11 03:18:34 kurkobuntu kernel: [41311.977624] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 03:18:43 kurkobuntu kernel: [41320.770355] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.145.225.22 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=57 ID=64827 DF PROTO=TCP SPT=42023 DPT=53290 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 11 03:18:46 kurkobuntu kernel: [41323.755444] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.145.225.22 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=57 ID=64828 DF PROTO=TCP SPT=42023 DPT=53290 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 11 03:18:52 kurkobuntu kernel: [41329.756702] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.145.225.22 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=57 ID=64829 DF PROTO=TCP SPT=42023 DPT=53290 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 11 03:48:26 kurkobuntu kernel: [43104.003735] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 03:48:28 kurkobuntu kernel: [43106.046146] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 03:48:32 kurkobuntu kernel: [43110.095690] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 03:54:40 kurkobuntu kernel: [43477.825553] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=94.202.106.128 DST=109.108.2.251 LEN=364 TOS=0x00 PREC=0x00 TTL=106 ID=28481 PROTO=UDP SPT=500 DPT=500 LEN=344 
Feb 11 03:54:40 kurkobuntu kernel: [43477.828213] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=94.202.106.128 DST=109.108.2.251 LEN=316 TOS=0x00 PREC=0x00 TTL=106 ID=28482 PROTO=UDP SPT=500 DPT=500 LEN=296 
Feb 11 03:59:06 kurkobuntu ntpd[2530]: kernel time sync status change 2001
Feb 11 04:00:01 kurkobuntu CRON[6017]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Feb 11 04:03:28 kurkobuntu kernel: [44005.364991] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=71.115.55.230 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=43 ID=7122 DF PROTO=TCP SPT=50117 DPT=39573 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 04:03:28 kurkobuntu kernel: [44005.866830] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=71.115.55.230 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=42 ID=5670 DF PROTO=TCP SPT=50118 DPT=39573 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 04:06:50 kurkobuntu kernel: [44208.047841] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=112.201.150.107 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=37 ID=0 DF PROTO=TCP SPT=56927 DPT=60060 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 04:06:51 kurkobuntu kernel: [44209.023518] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=219.108.152.105 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=102 ID=12735 DF PROTO=TCP SPT=60503 DPT=49316 WINDOW=8192 RES=0x00 ACK SYN URGP=0 
Feb 11 04:06:57 kurkobuntu kernel: [44215.024364] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=219.108.152.105 DST=109.108.2.251 LEN=56 TOS=0x00 PREC=0x00 TTL=100 ID=14359 DF PROTO=TCP SPT=60510 DPT=49316 WINDOW=8192 RES=0x00 ACK SYN URGP=0 
Feb 11 04:06:57 kurkobuntu kernel: [44215.111075] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=219.108.152.105 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=100 ID=14367 DF PROTO=TCP SPT=60511 DPT=58006 WINDOW=8192 RES=0x00 ACK SYN URGP=0 
Feb 11 04:07:00 kurkobuntu kernel: [44218.095949] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=219.108.152.105 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=103 ID=14810 DF PROTO=TCP SPT=60515 DPT=58006 WINDOW=8192 RES=0x00 ACK SYN URGP=0 
Feb 11 04:07:06 kurkobuntu kernel: [44224.125287] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=219.108.152.105 DST=109.108.2.251 LEN=56 TOS=0x00 PREC=0x00 TTL=101 ID=15905 DF PROTO=TCP SPT=60524 DPT=58006 WINDOW=8192 RES=0x00 ACK SYN URGP=0 
Feb 11 04:07:21 kurkobuntu kernel: [44239.159369] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=219.108.152.105 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=102 ID=18363 DF PROTO=TCP SPT=60564 DPT=58006 WINDOW=8192 RES=0x00 ACK SYN URGP=0 
Feb 11 04:13:03 kurkobuntu pulseaudio[2227]: ratelimit.c: 218 events suppressed
Feb 11 04:17:02 kurkobuntu CRON[6426]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 11 04:17:24 kurkobuntu kernel: [44841.379931] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=109.187.12.153 DST=109.108.2.251 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=18426 DF PROTO=TCP SPT=4431 DPT=36160 WINDOW=65535 RES=0x00 SYN URGP=0 
Feb 11 04:17:24 kurkobuntu kernel: [44841.387686] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=109.187.12.153 DST=109.108.2.251 LEN=47 TOS=0x00 PREC=0x00 TTL=111 ID=18428 PROTO=UDP SPT=5326 DPT=36160 LEN=27 
Feb 11 04:17:27 kurkobuntu kernel: [44844.335379] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=109.187.12.153 DST=109.108.2.251 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=18438 DF PROTO=TCP SPT=4431 DPT=36160 WINDOW=65535 RES=0x00 SYN URGP=0 
Feb 11 04:17:33 kurkobuntu kernel: [44850.369757] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=109.187.12.153 DST=109.108.2.251 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=18451 DF PROTO=TCP SPT=4431 DPT=36160 WINDOW=65535 RES=0x00 SYN URGP=0 
Feb 11 04:18:28 kurkobuntu kernel: [44905.592342] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=130 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=110 
Feb 11 04:18:30 kurkobuntu kernel: [44907.638156] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=130 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=110 
Feb 11 04:18:34 kurkobuntu kernel: [44911.698175] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=130 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=110 
Feb 11 04:31:37 kurkobuntu kernel: [45694.561418] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=220.136.55.144 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=106 ID=8034 DF PROTO=TCP SPT=63020 DPT=35540 WINDOW=0 RES=0x00 ACK URGP=0 
Feb 11 04:32:53 kurkobuntu kernel: [45770.815747] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=220.136.55.144 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=106 ID=15392 DF PROTO=TCP SPT=63020 DPT=35540 WINDOW=0 RES=0x00 ACK URGP=0 
Feb 11 04:47:15 kurkobuntu kernel: [46632.715547] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=94.202.106.128 DST=109.108.2.251 LEN=364 TOS=0x00 PREC=0x00 TTL=106 ID=4957 PROTO=UDP SPT=500 DPT=500 LEN=344 
Feb 11 04:47:15 kurkobuntu kernel: [46632.718689] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=94.202.106.128 DST=109.108.2.251 LEN=316 TOS=0x00 PREC=0x00 TTL=106 ID=4958 PROTO=UDP SPT=500 DPT=500 LEN=296 
Feb 11 04:48:30 kurkobuntu kernel: [46707.287622] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=130 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=110 
Feb 11 04:48:32 kurkobuntu kernel: [46709.306851] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=130 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=110 
Feb 11 04:48:36 kurkobuntu kernel: [46713.385260] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=130 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=110 
Feb 11 04:59:10 kurkobuntu dhclient: DHCPREQUEST of 109.108.2.251 on eth0 to 213.243.153.175 port 67
Feb 11 04:59:10 kurkobuntu dhclient: DHCPACK of 109.108.2.251 from 213.243.153.175
Feb 11 04:59:10 kurkobuntu dhclient: bound to 109.108.2.251 -- renewal in 7600 seconds.
Feb 11 05:00:01 kurkobuntu CRON[7470]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Feb 11 05:00:03 kurkobuntu postfix/pickup[7434]: 33E284600D1: uid=0 from=<root>
Feb 11 05:00:03 kurkobuntu postfix/cleanup[8632]: 33E284600D1: message-id=<20110211030003.33E284600D1@kurkobuntu>
Feb 11 05:00:03 kurkobuntu postfix/qmgr[10753]: 33E284600D1: from=<root@kurkobuntu>, size=751, nrcpt=1 (queue active)
Feb 11 05:00:03 kurkobuntu postfix/local[8634]: 33E284600D1: to=<root@kurkobuntu>, orig_to=<root>, relay=local, delay=0.34, delays=0.23/0.02/0/0.08, dsn=2.0.0, status=sent (delivered to mailbox)
Feb 11 05:00:03 kurkobuntu postfix/qmgr[10753]: 33E284600D1: removed
Feb 11 05:03:44 kurkobuntu kernel: [47621.540176] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=18.228.0.150 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=50 ID=22604 DF PROTO=TCP SPT=50048 DPT=41207 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 05:03:45 kurkobuntu kernel: [47622.533103] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=18.228.0.150 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=50 ID=3191 DF PROTO=TCP SPT=50048 DPT=41207 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 05:03:46 kurkobuntu kernel: [47623.533551] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=18.228.0.150 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=50 ID=20006 DF PROTO=TCP SPT=50048 DPT=41207 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 05:03:47 kurkobuntu kernel: [47624.534151] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=18.228.0.150 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=50 ID=64888 DF PROTO=TCP SPT=50048 DPT=41207 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 05:03:48 kurkobuntu kernel: [47625.534711] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=18.228.0.150 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=50 ID=10287 DF PROTO=TCP SPT=50048 DPT=41207 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 05:03:49 kurkobuntu kernel: [47626.535502] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=18.228.0.150 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=50 ID=8998 DF PROTO=TCP SPT=50048 DPT=41207 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 05:03:51 kurkobuntu kernel: [47628.536497] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=18.228.0.150 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=50 ID=43118 DF PROTO=TCP SPT=50048 DPT=41207 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 05:03:55 kurkobuntu kernel: [47632.539098] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=18.228.0.150 DST=109.108.2.251 LEN=48 TOS=0x00 PREC=0x00 TTL=50 ID=11282 DF PROTO=TCP SPT=50048 DPT=41207 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 05:03:56 kurkobuntu kernel: [47633.504018] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=108.32.97.233 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=43 ID=20807 DF PROTO=TCP SPT=61359 DPT=57416 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 05:03:56 kurkobuntu kernel: [47634.028343] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=108.32.97.233 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=42 ID=57678 DF PROTO=TCP SPT=61360 DPT=57416 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 05:04:18 kurkobuntu kernel: [47655.866596] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=202.109.115.169 DST=109.108.2.251 LEN=438 TOS=0x00 PREC=0x00 TTL=37 ID=0 DF PROTO=UDP SPT=5060 DPT=5060 LEN=418 
Feb 11 05:05:54 kurkobuntu kernel: [47751.619648] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=89.253.110.131 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=40228 DF PROTO=TCP SPT=53797 DPT=43517 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 05:05:54 kurkobuntu kernel: [47752.116739] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=89.253.110.131 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=6498 DF PROTO=TCP SPT=65001 DPT=43517 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 05:12:00 kurkobuntu kernel: [48117.861390] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=67.175.226.20 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=44 ID=14069 PROTO=TCP SPT=60034 DPT=55282 WINDOW=0 RES=0x00 ACK RST URGP=0 
Feb 11 05:12:04 kurkobuntu kernel: [48121.398591] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=69.125.203.176 DST=109.108.2.251 LEN=88 TOS=0x00 PREC=0x00 TTL=47 ID=40372 PROTO=ICMP TYPE=3 CODE=1 [SRC=109.108.2.251 DST=192.168.1.100 LEN=60 TOS=0x00 PREC=0x00 TTL=46 ID=20340 DF PROTO=TCP SPT=33114 DPT=16984 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Feb 11 05:12:04 kurkobuntu kernel: [48121.510021] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=190.230.210.208 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=237 ID=17432 PROTO=TCP SPT=13557 DPT=36610 WINDOW=0 RES=0x00 ACK RST URGP=0 
Feb 11 05:12:04 kurkobuntu kernel: [48121.992031] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=114.76.188.190 DST=109.108.2.251 LEN=88 TOS=0x00 PREC=0x00 TTL=41 ID=20804 PROTO=ICMP TYPE=3 CODE=1 [SRC=109.108.2.251 DST=192.168.1.10 LEN=60 TOS=0x00 PREC=0x00 TTL=39 ID=52603 DF PROTO=TCP SPT=33528 DPT=6881 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Feb 11 05:12:05 kurkobuntu kernel: [48122.260318] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=89.201.151.221 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=114 ID=635 PROTO=TCP SPT=10491 DPT=43153 WINDOW=0 RES=0x00 ACK RST URGP=0 
Feb 11 05:12:05 kurkobuntu kernel: [48122.917946] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=99.141.199.25 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=46 ID=17911 PROTO=TCP SPT=61681 DPT=51049 WINDOW=0 RES=0x00 ACK RST FIN URGP=0 
Feb 11 05:12:06 kurkobuntu kernel: [48123.390849] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=79.176.18.68 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=234 ID=6911 PROTO=TCP SPT=17513 DPT=42580 WINDOW=0 RES=0x00 ACK RST URGP=0 
Feb 11 05:12:06 kurkobuntu kernel: [48123.874399] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=67.175.226.20 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=44 ID=16433 PROTO=TCP SPT=60034 DPT=55282 WINDOW=0 RES=0x00 ACK RST URGP=0 
Feb 11 05:12:10 kurkobuntu kernel: [48127.518684] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=190.230.210.208 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=237 ID=17433 PROTO=TCP SPT=13558 DPT=36610 WINDOW=0 RES=0x00 ACK RST URGP=0 
Feb 11 05:12:17 kurkobuntu kernel: [48134.294288] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=89.201.151.221 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=114 ID=636 PROTO=TCP SPT=10492 DPT=43153 WINDOW=0 RES=0x00 ACK RST URGP=0 
Feb 11 05:12:22 kurkobuntu kernel: [48139.547400] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=190.230.210.208 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=237 ID=17434 PROTO=TCP SPT=13559 DPT=36610 WINDOW=0 RES=0x00 ACK RST URGP=0 
Feb 11 05:12:43 kurkobuntu kernel: [48160.411285] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.237.161.238 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=243 ID=54417 PROTO=TCP SPT=14380 DPT=55902 WINDOW=0 RES=0x00 ACK RST URGP=0 
Feb 11 05:13:03 kurkobuntu kernel: [48180.266815] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=201.246.143.109 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=233 ID=7763 PROTO=TCP SPT=15944 DPT=54412 WINDOW=0 RES=0x00 ACK RST URGP=0 
Feb 11 05:13:23 kurkobuntu kernel: [48200.663504] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=89.201.147.227 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=114 ID=6327 PROTO=TCP SPT=15012 DPT=56829 WINDOW=0 RES=0x00 ACK RST URGP=0 
Feb 11 05:13:45 kurkobuntu kernel: [48222.804982] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=78.70.35.38 DST=109.108.2.251 LEN=88 TOS=0x00 PREC=0x00 TTL=51 ID=9135 PROTO=ICMP TYPE=3 CODE=1 [SRC=109.108.2.251 DST=192.168.1.118 LEN=60 TOS=0x00 PREC=0x00 TTL=47 ID=12413 DF PROTO=TCP SPT=36852 DPT=19364 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Feb 11 05:14:06 kurkobuntu kernel: [48243.857069] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=78.70.35.38 DST=109.108.2.251 LEN=88 TOS=0x00 PREC=0x00 TTL=51 ID=9138 PROTO=ICMP TYPE=3 CODE=1 [SRC=109.108.2.251 DST=192.168.1.118 LEN=60 TOS=0x00 PREC=0x00 TTL=47 ID=12416 DF PROTO=TCP SPT=36852 DPT=19364 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Feb 11 05:14:24 kurkobuntu kernel: [48261.679887] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=98.207.144.32 DST=109.108.2.251 LEN=88 TOS=0x00 PREC=0x00 TTL=44 ID=32415 PROTO=ICMP TYPE=3 CODE=1 [SRC=109.108.2.251 DST=192.168.1.113 LEN=60 TOS=0x00 PREC=0x20 TTL=43 ID=29356 DF PROTO=TCP SPT=51113 DPT=31426 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Feb 11 05:14:45 kurkobuntu kernel: [48282.423957] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=173.65.226.33 DST=109.108.2.251 LEN=56 TOS=0x00 PREC=0x00 TTL=106 ID=13470 DF PROTO=TCP SPT=62558 DPT=50359 WINDOW=8192 RES=0x00 ACK SYN URGP=0 
Feb 11 05:15:03 kurkobuntu kernel: [48300.419004] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=74.124.42.180 DST=109.108.2.251 LEN=88 TOS=0x00 PREC=0x00 TTL=45 ID=12315 PROTO=ICMP TYPE=3 CODE=1 [SRC=109.108.2.251 DST=192.168.1.138 LEN=60 TOS=0x00 PREC=0x00 TTL=44 ID=46905 DF PROTO=TCP SPT=36178 DPT=51413 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Feb 11 05:15:21 kurkobuntu kernel: [48319.090356] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=75.51.161.153 DST=109.108.2.251 LEN=56 TOS=0x00 PREC=0x00 TTL=233 ID=65180 PROTO=ICMP TYPE=3 CODE=13 [SRC=109.108.2.251 DST=75.51.161.153 LEN=60 TOS=0x00 PREC=0x00 TTL=42 ID=32844 PROTO=TCP INCOMPLETE [8 bytes] ] 
Feb 11 05:15:41 kurkobuntu kernel: [48338.543799] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=99.247.114.48 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=21591 DF PROTO=TCP SPT=62508 DPT=44955 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 05:16:02 kurkobuntu kernel: [48359.599480] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=99.247.114.48 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=110 ID=23065 DF PROTO=TCP SPT=62563 DPT=44955 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 05:16:26 kurkobuntu kernel: [48383.352396] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=41.249.45.177 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=50 ID=438 PROTO=TCP SPT=12076 DPT=34549 WINDOW=0 RES=0x00 ACK RST FIN URGP=0 
Feb 11 05:16:46 kurkobuntu kernel: [48403.282116] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=41.235.76.253 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=232 ID=25825 PROTO=TCP SPT=13832 DPT=55259 WINDOW=0 RES=0x00 ACK RST URGP=0 
Feb 11 05:17:01 kurkobuntu CRON[8664]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 11 05:17:02 kurkobuntu kernel: [48420.038159] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=41.234.58.197 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=236 ID=23502 PROTO=TCP SPT=21236 DPT=44613 WINDOW=0 RES=0x00 ACK RST URGP=0 
Feb 11 05:17:24 kurkobuntu kernel: [48441.346384] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=24.20.129.255 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=106 ID=304 DF PROTO=TCP SPT=64708 DPT=35638 WINDOW=0 RES=0x00 ACK RST URGP=0 
Feb 11 05:17:44 kurkobuntu kernel: [48462.063255] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=220.136.55.144 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=107 ID=5812 DF PROTO=TCP SPT=63020 DPT=60234 WINDOW=0 RES=0x00 ACK URGP=0 
Feb 11 05:17:51 kurkobuntu kernel: [48468.837223] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=122.175.82.80 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=241 ID=30346 PROTO=TCP SPT=18583 DPT=43306 WINDOW=0 RES=0x00 ACK RST URGP=0 
Feb 11 05:18:01 kurkobuntu kernel: [48478.472299] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=77.236.8.119 DST=109.108.2.251 LEN=88 TOS=0x00 PREC=0x00 TTL=53 ID=9465 PROTO=ICMP TYPE=3 CODE=1 [SRC=109.108.2.251 DST=192.168.1.127 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=47169 DF PROTO=TCP SPT=52589 DPT=62923 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Feb 11 05:18:22 kurkobuntu kernel: [48499.791955] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.145.225.22 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=57 ID=11447 DF PROTO=TCP SPT=38696 DPT=53290 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 11 05:18:24 kurkobuntu kernel: [48501.395986] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=89.201.147.221 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=114 ID=16166 PROTO=TCP SPT=29207 DPT=50111 WINDOW=0 RES=0x00 ACK RST URGP=0 
Feb 11 05:18:25 kurkobuntu kernel: [48502.789569] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.145.225.22 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=57 ID=11448 DF PROTO=TCP SPT=38696 DPT=53290 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 11 05:18:27 kurkobuntu kernel: [48504.982610] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 05:18:29 kurkobuntu kernel: [48507.028004] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 05:18:31 kurkobuntu kernel: [48508.789423] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.145.225.22 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=57 ID=11449 DF PROTO=TCP SPT=38696 DPT=53290 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 11 05:18:33 kurkobuntu kernel: [48511.040019] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 05:18:43 kurkobuntu kernel: [48520.792799] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.145.225.22 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=57 ID=44051 DF PROTO=TCP SPT=53641 DPT=53290 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 11 05:18:46 kurkobuntu kernel: [48523.789142] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.145.225.22 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=57 ID=44052 DF PROTO=TCP SPT=53641 DPT=53290 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 11 05:18:46 kurkobuntu kernel: [48523.943444] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.80.186.147 DST=109.108.2.251 LEN=88 TOS=0x00 PREC=0x00 TTL=44 ID=64080 PROTO=ICMP TYPE=3 CODE=1 [SRC=109.108.2.251 DST=192.168.1.115 LEN=60 TOS=0x18 PREC=0xA0 TTL=49 ID=11850 DF PROTO=TCP SPT=48017 DPT=16617 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Feb 11 05:18:52 kurkobuntu kernel: [48529.788973] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.145.225.22 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=57 ID=44053 DF PROTO=TCP SPT=53641 DPT=53290 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 11 05:19:12 kurkobuntu kernel: [48549.862332] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=184.59.29.3 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=107 ID=14211 PROTO=TCP SPT=63832 DPT=34631 WINDOW=0 RES=0x00 ACK RST URGP=0 
Feb 11 05:19:17 kurkobuntu kernel: [48554.607443] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=220.136.55.144 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=107 ID=12145 DF PROTO=TCP SPT=63020 DPT=60234 WINDOW=0 RES=0x00 ACK URGP=0 
Feb 11 05:21:06 kurkobuntu pulseaudio[2227]: ratelimit.c: 220 events suppressed
Feb 11 05:21:08 kurkobuntu kernel: [48665.688736] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=93.158.110.33 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=TCP SPT=80 DPT=44295 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 05:21:15 kurkobuntu kernel: [48672.494388] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=93.158.110.33 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=TCP SPT=80 DPT=44295 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 05:21:34 kurkobuntu kernel: [48691.564608] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.240.78.165 DST=109.108.2.251 LEN=88 TOS=0x00 PREC=0x00 TTL=50 ID=43962 PROTO=ICMP TYPE=3 CODE=1 [SRC=109.108.2.251 DST=192.168.1.2 LEN=60 TOS=0x00 PREC=0x00 TTL=50 ID=44972 DF PROTO=TCP SPT=60102 DPT=40728 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Feb 11 05:21:37 kurkobuntu kernel: [48694.565281] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.240.78.165 DST=109.108.2.251 LEN=88 TOS=0x00 PREC=0x00 TTL=50 ID=43963 PROTO=ICMP TYPE=3 CODE=1 [SRC=109.108.2.251 DST=192.168.1.2 LEN=60 TOS=0x00 PREC=0x00 TTL=50 ID=44973 DF PROTO=TCP SPT=60102 DPT=40728 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Feb 11 05:21:37 kurkobuntu kernel: [48694.570816] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.196.122.247 DST=109.108.2.251 LEN=88 TOS=0x00 PREC=0x00 TTL=53 ID=40994 PROTO=ICMP TYPE=3 CODE=1 [SRC=109.108.2.251 DST=192.168.1.100 LEN=60 TOS=0x00 PREC=0x00 TTL=54 ID=25652 DF PROTO=TCP SPT=34512 DPT=64289 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Feb 11 05:21:40 kurkobuntu kernel: [48697.566334] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.196.122.247 DST=109.108.2.251 LEN=88 TOS=0x00 PREC=0x00 TTL=53 ID=40995 PROTO=ICMP TYPE=3 CODE=1 [SRC=109.108.2.251 DST=192.168.1.100 LEN=60 TOS=0x00 PREC=0x00 TTL=54 ID=25653 DF PROTO=TCP SPT=34512 DPT=64289 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Feb 11 05:21:46 kurkobuntu kernel: [48703.585177] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.196.122.247 DST=109.108.2.251 LEN=88 TOS=0x00 PREC=0x00 TTL=53 ID=40996 PROTO=ICMP TYPE=3 CODE=1 [SRC=109.108.2.251 DST=192.168.1.100 LEN=60 TOS=0x00 PREC=0x00 TTL=54 ID=25654 DF PROTO=TCP SPT=34512 DPT=64289 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Feb 11 05:21:55 kurkobuntu kernel: [48712.609523] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.240.78.165 DST=109.108.2.251 LEN=88 TOS=0x00 PREC=0x00 TTL=50 ID=43965 PROTO=ICMP TYPE=3 CODE=1 [SRC=109.108.2.251 DST=192.168.1.2 LEN=60 TOS=0x00 PREC=0x00 TTL=50 ID=44975 DF PROTO=TCP SPT=60102 DPT=40728 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Feb 11 05:22:17 kurkobuntu kernel: [48734.857986] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=208.57.160.77 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=229 ID=30922 PROTO=TCP SPT=21740 DPT=34289 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 05:22:21 kurkobuntu kernel: [48739.071137] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=69.136.13.178 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=235 ID=10288 PROTO=TCP SPT=6112 DPT=34070 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 05:25:09 kurkobuntu kernel: [48906.333834] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=220.136.55.144 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=104 ID=32679 DF PROTO=TCP SPT=63020 DPT=35867 WINDOW=0 RES=0x00 ACK URGP=0 
Feb 11 05:41:30 kurkobuntu ntpd[2530]: kernel time sync status change 6001
Feb 11 05:48:27 kurkobuntu kernel: [50305.205831] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 05:48:30 kurkobuntu kernel: [50307.226079] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 05:48:34 kurkobuntu kernel: [50311.270085] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 05:58:34 kurkobuntu ntpd[2530]: kernel time sync status change 2001
Feb 11 06:00:01 kurkobuntu CRON[8737]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Feb 11 06:03:28 kurkobuntu kernel: [51205.565075] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=71.115.55.230 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=42 ID=37700 DF PROTO=TCP SPT=50118 DPT=39573 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 06:03:28 kurkobuntu kernel: [51206.064061] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=71.115.55.230 DST=109.108.2.251 LEN=64 TOS=0x00 PREC=0x00 TTL=42 ID=49994 DF PROTO=TCP SPT=50119 DPT=39573 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 06:17:02 kurkobuntu CRON[9141]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 11 06:17:43 kurkobuntu kernel: [52060.452419] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=156.34.89.150 DST=109.108.2.251 LEN=52 TOS=0x00 PREC=0x00 TTL=109 ID=20277 DF PROTO=TCP SPT=50709 DPT=36160 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 06:17:43 kurkobuntu kernel: [52060.458181] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=156.34.89.150 DST=109.108.2.251 LEN=47 TOS=0x00 PREC=0x00 TTL=112 ID=20279 PROTO=UDP SPT=32201 DPT=36160 LEN=27 
Feb 11 06:17:46 kurkobuntu kernel: [52063.452601] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=156.34.89.150 DST=109.108.2.251 LEN=52 TOS=0x00 PREC=0x00 TTL=109 ID=20287 DF PROTO=TCP SPT=50709 DPT=36160 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 06:17:52 kurkobuntu kernel: [52069.449050] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=156.34.89.150 DST=109.108.2.251 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=20316 DF PROTO=TCP SPT=50709 DPT=36160 WINDOW=8192 RES=0x00 SYN URGP=0 
Feb 11 06:18:26 kurkobuntu kernel: [52103.630573] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 06:18:28 kurkobuntu kernel: [52105.695940] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 06:18:32 kurkobuntu kernel: [52109.735941] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 06:25:01 kurkobuntu CRON[9161]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Feb 11 06:25:49 kurkobuntu kernel: [52547.134909] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=21886 DF PROTO=TCP SPT=23173 DPT=52191 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:25:49 kurkobuntu kernel: [52547.140614] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=29442 DF PROTO=TCP SPT=23173 DPT=52191 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:26:16 kurkobuntu kernel: [52574.053331] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=10402 DF PROTO=TCP SPT=23173 DPT=46215 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:26:16 kurkobuntu kernel: [52574.056301] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=14800 DF PROTO=TCP SPT=23173 DPT=46215 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:26:39 kurkobuntu kernel: [52597.034630] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=45908 DF PROTO=TCP SPT=23173 DPT=47635 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:26:39 kurkobuntu kernel: [52597.034871] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=57964 DF PROTO=TCP SPT=23173 DPT=47635 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:26:39 kurkobuntu kernel: [52597.041034] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=37150 DF PROTO=TCP SPT=23173 DPT=47635 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:26:39 kurkobuntu kernel: [52597.041502] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=1137 DF PROTO=TCP SPT=23173 DPT=47635 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:26:43 kurkobuntu kernel: [52600.458147] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=174.1.199.201 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=13752 PROTO=TCP SPT=40576 DPT=60060 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:34:11 kurkobuntu kernel: [53049.091661] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=9286 DF PROTO=TCP SPT=23173 DPT=50178 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:34:11 kurkobuntu kernel: [53049.094305] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=28942 DF PROTO=TCP SPT=23173 DPT=50178 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:34:11 kurkobuntu kernel: [53049.095804] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=32552 DF PROTO=TCP SPT=23173 DPT=50178 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:34:11 kurkobuntu kernel: [53049.096479] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=20093 DF PROTO=TCP SPT=23173 DPT=50178 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:34:11 kurkobuntu kernel: [53049.097025] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=23643 DF PROTO=TCP SPT=23173 DPT=50178 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:34:11 kurkobuntu kernel: [53049.097775] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=12876 DF PROTO=TCP SPT=23173 DPT=50178 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:34:11 kurkobuntu kernel: [53049.099613] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=24658 DF PROTO=TCP SPT=23173 DPT=50178 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:35:01 kurkobuntu kernel: [53099.054192] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=15129 DF PROTO=TCP SPT=23173 DPT=58422 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:35:01 kurkobuntu kernel: [53099.055088] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=35653 DF PROTO=TCP SPT=23173 DPT=58422 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:35:01 kurkobuntu kernel: [53099.056590] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=34640 DF PROTO=TCP SPT=23173 DPT=58422 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:35:01 kurkobuntu kernel: [53099.076324] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=10879 DF PROTO=TCP SPT=23173 DPT=58422 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:35:01 kurkobuntu kernel: [53099.080068] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=36153 DF PROTO=TCP SPT=23173 DPT=58422 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:35:52 kurkobuntu kernel: [53150.049904] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=39026 DF PROTO=TCP SPT=23173 DPT=54074 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:35:52 kurkobuntu kernel: [53150.069162] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=4149 DF PROTO=TCP SPT=23173 DPT=54074 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:35:52 kurkobuntu kernel: [53150.070735] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=17011 DF PROTO=TCP SPT=23173 DPT=54074 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:36:23 kurkobuntu kernel: [53181.086025] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=63254 DF PROTO=TCP SPT=23173 DPT=44209 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:36:51 kurkobuntu kernel: [53209.071917] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=27049 DF PROTO=TCP SPT=23173 DPT=54472 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:36:51 kurkobuntu kernel: [53209.095862] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=24709 DF PROTO=TCP SPT=23173 DPT=54472 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:46:17 kurkobuntu kernel: [53775.071663] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=23622 DF PROTO=TCP SPT=23173 DPT=59766 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:46:17 kurkobuntu kernel: [53775.074980] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=42861 DF PROTO=TCP SPT=23173 DPT=59766 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:46:17 kurkobuntu kernel: [53775.078851] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=53877 DF PROTO=TCP SPT=23173 DPT=59766 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:46:17 kurkobuntu kernel: [53775.086881] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=32328 DF PROTO=TCP SPT=23173 DPT=59766 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:46:17 kurkobuntu kernel: [53775.090213] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=40755 DF PROTO=TCP SPT=23173 DPT=59766 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:46:17 kurkobuntu kernel: [53775.090828] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=62216 DF PROTO=TCP SPT=23173 DPT=59766 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:47:08 kurkobuntu kernel: [53826.146022] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=5892 DF PROTO=TCP SPT=23173 DPT=35156 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:48:26 kurkobuntu kernel: [53903.424158] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 06:48:28 kurkobuntu kernel: [53905.493835] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 06:48:32 kurkobuntu kernel: [53909.504092] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 06:50:32 kurkobuntu kernel: [54030.058947] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=14002 DF PROTO=TCP SPT=23173 DPT=47432 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:50:32 kurkobuntu kernel: [54030.059668] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=3777 DF PROTO=TCP SPT=23173 DPT=47432 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:50:56 kurkobuntu kernel: [54054.124527] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=19278 DF PROTO=TCP SPT=23173 DPT=60403 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:50:56 kurkobuntu kernel: [54054.125522] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=36200 DF PROTO=TCP SPT=23173 DPT=60403 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:50:56 kurkobuntu kernel: [54054.144637] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=18689 DF PROTO=TCP SPT=23173 DPT=60403 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:50:56 kurkobuntu kernel: [54054.146635] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=57123 DF PROTO=TCP SPT=23173 DPT=60403 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:51:05 kurkobuntu kernel: [54062.314888] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=93.158.110.33 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=TCP SPT=80 DPT=44240 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:51:05 kurkobuntu kernel: [54062.754788] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=93.158.110.33 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=TCP SPT=80 DPT=44240 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:51:06 kurkobuntu kernel: [54063.634695] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=93.158.110.33 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=TCP SPT=80 DPT=44240 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:51:08 kurkobuntu kernel: [54065.398631] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=93.158.110.33 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=TCP SPT=80 DPT=44240 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:51:11 kurkobuntu kernel: [54068.925381] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=93.158.110.33 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=TCP SPT=80 DPT=44240 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:51:18 kurkobuntu kernel: [54075.982924] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=93.158.110.33 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=TCP SPT=80 DPT=44240 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 06:52:20 kurkobuntu kernel: [54137.747785] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=69.253.117.253 DST=109.108.2.251 LEN=123 TOS=0x00 PREC=0x00 TTL=41 ID=18589 PROTO=ICMP TYPE=3 CODE=1 [SRC=109.108.2.251 DST=192.168.1.102 LEN=95 TOS=0x00 PREC=0x20 TTL=44 ID=0 DF PROTO=UDP SPT=60060 DPT=45632 LEN=75 ] 
Feb 11 06:56:02 kurkobuntu kernel: [54360.033234] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=60.13.174.54 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=95 ID=47814 PROTO=TCP SPT=6000 DPT=3306 WINDOW=16384 RES=0x00 SYN URGP=0 
Feb 11 07:00:01 kurkobuntu CRON[9221]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Feb 11 07:01:05 kurkobuntu kernel: [54663.107514] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=29502 DF PROTO=TCP SPT=23173 DPT=54527 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:01:05 kurkobuntu kernel: [54663.111682] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=23628 DF PROTO=TCP SPT=23173 DPT=54527 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:01:05 kurkobuntu kernel: [54663.112258] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=23130 DF PROTO=TCP SPT=23173 DPT=54527 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:01:05 kurkobuntu kernel: [54663.112756] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=53537 DF PROTO=TCP SPT=23173 DPT=54527 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:01:05 kurkobuntu kernel: [54663.114507] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=45428 DF PROTO=TCP SPT=23173 DPT=54527 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:01:05 kurkobuntu kernel: [54663.115310] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=22370 DF PROTO=TCP SPT=23173 DPT=54527 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:01:05 kurkobuntu kernel: [54663.116135] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=28761 DF PROTO=TCP SPT=23173 DPT=54527 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:01:05 kurkobuntu kernel: [54663.117438] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=41513 DF PROTO=TCP SPT=23173 DPT=54527 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:01:05 kurkobuntu kernel: [54663.118338] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=49196 DF PROTO=TCP SPT=23173 DPT=54527 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:01:05 kurkobuntu kernel: [54663.121717] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=322 DF PROTO=TCP SPT=23173 DPT=54527 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:01:30 kurkobuntu kernel: [54688.051583] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=39614 DF PROTO=TCP SPT=23173 DPT=51111 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:02:22 kurkobuntu kernel: [54740.130973] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=10816 DF PROTO=TCP SPT=23173 DPT=41355 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:02:22 kurkobuntu kernel: [54740.131570] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=58709 DF PROTO=TCP SPT=23173 DPT=41355 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:02:47 kurkobuntu kernel: [54765.135935] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=58798 DF PROTO=TCP SPT=23173 DPT=58377 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:02:47 kurkobuntu kernel: [54765.138462] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=7319 DF PROTO=TCP SPT=23173 DPT=58377 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:03:17 kurkobuntu kernel: [54795.138226] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=29656 DF PROTO=TCP SPT=23173 DPT=41877 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:05:50 kurkobuntu dhclient: DHCPREQUEST of 109.108.2.251 on eth0 to 213.243.153.175 port 67
Feb 11 07:05:50 kurkobuntu dhclient: DHCPACK of 109.108.2.251 from 213.243.153.175
Feb 11 07:05:50 kurkobuntu dhclient: bound to 109.108.2.251 -- renewal in 7910 seconds.
Feb 11 07:06:42 kurkobuntu kernel: [55000.123830] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=50686 DF PROTO=TCP SPT=23173 DPT=44169 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:06:42 kurkobuntu kernel: [55000.125806] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=43951 DF PROTO=TCP SPT=23173 DPT=44169 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:06:42 kurkobuntu kernel: [55000.128101] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=60664 DF PROTO=TCP SPT=23173 DPT=44169 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:06:42 kurkobuntu kernel: [55000.132205] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=8426 DF PROTO=TCP SPT=23173 DPT=44169 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:06:42 kurkobuntu kernel: [55000.137240] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=47008 DF PROTO=TCP SPT=23173 DPT=44169 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:06:42 kurkobuntu kernel: [55000.137884] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=1473 DF PROTO=TCP SPT=23173 DPT=44169 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:06:42 kurkobuntu kernel: [55000.140662] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=8080 DF PROTO=TCP SPT=23173 DPT=44169 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:06:42 kurkobuntu kernel: [55000.141528] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=36091 DF PROTO=TCP SPT=23173 DPT=44169 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:06:42 kurkobuntu kernel: [55000.141835] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=61829 DF PROTO=TCP SPT=23173 DPT=44169 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:06:42 kurkobuntu kernel: [55000.142710] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=39380 DF PROTO=TCP SPT=23173 DPT=44169 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:06:55 kurkobuntu ntpd[2530]: kernel time sync status change 6001
Feb 11 07:07:15 kurkobuntu kernel: [55033.035620] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=49689 DF PROTO=TCP SPT=23173 DPT=54725 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:07:38 kurkobuntu kernel: [55056.060107] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=21695 DF PROTO=TCP SPT=23173 DPT=36871 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:08:04 kurkobuntu kernel: [55082.067958] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=58437 DF PROTO=TCP SPT=23173 DPT=52400 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:08:04 kurkobuntu kernel: [55082.070632] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=50440 DF PROTO=TCP SPT=23173 DPT=52400 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:09:56 kurkobuntu kernel: [55194.050329] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=5850 DF PROTO=TCP SPT=23173 DPT=56006 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:09:56 kurkobuntu kernel: [55194.054284] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=31706 DF PROTO=TCP SPT=23173 DPT=56006 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:09:56 kurkobuntu kernel: [55194.056977] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=50394 DF PROTO=TCP SPT=23173 DPT=56006 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:09:56 kurkobuntu kernel: [55194.058828] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=32682 DF PROTO=TCP SPT=23173 DPT=56006 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:09:56 kurkobuntu kernel: [55194.101910] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=36295 DF PROTO=TCP SPT=23173 DPT=56006 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:11:42 kurkobuntu kernel: [55300.101294] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=62179 DF PROTO=TCP SPT=23173 DPT=52343 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:11:42 kurkobuntu kernel: [55300.105227] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=60605 DF PROTO=TCP SPT=23173 DPT=52343 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:11:42 kurkobuntu kernel: [55300.110173] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=24967 DF PROTO=TCP SPT=23173 DPT=52343 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:11:42 kurkobuntu kernel: [55300.111739] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=38566 DF PROTO=TCP SPT=23173 DPT=52343 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:11:42 kurkobuntu kernel: [55300.114517] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=17629 DF PROTO=TCP SPT=23173 DPT=52343 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:11:42 kurkobuntu kernel: [55300.120330] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=53182 DF PROTO=TCP SPT=23173 DPT=52343 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:12:06 kurkobuntu kernel: [55324.084571] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=955 DF PROTO=TCP SPT=23173 DPT=58088 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:12:52 kurkobuntu kernel: [55370.146234] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=24523 DF PROTO=TCP SPT=23173 DPT=60551 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:12:52 kurkobuntu kernel: [55370.147057] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=36321 DF PROTO=TCP SPT=23173 DPT=60551 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:13:23 kurkobuntu kernel: [55401.093560] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=5971 DF PROTO=TCP SPT=23173 DPT=54832 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:13:23 kurkobuntu kernel: [55401.094679] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=42096 DF PROTO=TCP SPT=23173 DPT=54832 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:13:55 kurkobuntu kernel: [55433.114831] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=49758 DF PROTO=TCP SPT=23173 DPT=44025 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:14:17 kurkobuntu kernel: [55455.134971] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=6809 DF PROTO=TCP SPT=23173 DPT=55782 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:14:29 kurkobuntu kernel: [55466.640116] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=90.193.127.210 DST=109.108.2.251 LEN=88 TOS=0x00 PREC=0x00 TTL=240 ID=28889 PROTO=ICMP TYPE=3 CODE=1 [SRC=109.108.2.251 DST=192.168.0.2 LEN=60 TOS=0x00 PREC=0x00 TTL=47 ID=23111 DF PROTO=TCP SPT=49186 DPT=24001 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
Feb 11 07:15:19 kurkobuntu kernel: [55517.163583] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=18984 DF PROTO=TCP SPT=23173 DPT=56013 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:15:19 kurkobuntu kernel: [55517.167054] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=54785 DF PROTO=TCP SPT=23173 DPT=56013 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:15:45 kurkobuntu kernel: [55543.114012] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=5355 DF PROTO=TCP SPT=23173 DPT=36888 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:15:45 kurkobuntu kernel: [55543.118140] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=47339 DF PROTO=TCP SPT=23173 DPT=36888 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:16:07 kurkobuntu kernel: [55565.144636] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=1949 DF PROTO=TCP SPT=23173 DPT=53891 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:16:44 kurkobuntu kernel: [55602.200693] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=30151 DF PROTO=TCP SPT=23173 DPT=46424 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:16:44 kurkobuntu kernel: [55602.201113] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=9215 DF PROTO=TCP SPT=23173 DPT=46424 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:17:01 kurkobuntu CRON[9373]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 11 07:17:09 kurkobuntu kernel: [55627.143227] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=38718 DF PROTO=TCP SPT=23173 DPT=58239 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:18:22 kurkobuntu kernel: [55699.388121] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.145.225.22 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=57 ID=19802 DF PROTO=TCP SPT=32838 DPT=53290 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 11 07:18:25 kurkobuntu kernel: [55702.369850] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.145.225.22 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=57 ID=19803 DF PROTO=TCP SPT=32838 DPT=53290 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 11 07:18:26 kurkobuntu kernel: [55703.950058] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 07:18:28 kurkobuntu kernel: [55705.982051] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 07:18:31 kurkobuntu kernel: [55708.280704] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.145.225.22 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=57 ID=19804 DF PROTO=TCP SPT=32838 DPT=53290 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 11 07:18:32 kurkobuntu kernel: [55710.014720] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=82.181.223.84 DST=109.108.2.251 LEN=129 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=27758 DPT=36160 LEN=109 
Feb 11 07:18:43 kurkobuntu kernel: [55720.268927] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.145.225.22 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=57 ID=53530 DF PROTO=TCP SPT=45282 DPT=53290 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 11 07:18:46 kurkobuntu kernel: [55723.269828] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=83.145.225.22 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=57 ID=53531 DF PROTO=TCP SPT=45282 DPT=53290 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 11 07:20:06 kurkobuntu kernel: [55804.149989] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=45604 DF PROTO=TCP SPT=23173 DPT=54270 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:20:06 kurkobuntu kernel: [55804.153613] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=51275 DF PROTO=TCP SPT=23173 DPT=54270 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:20:06 kurkobuntu kernel: [55804.164166] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=30746 DF PROTO=TCP SPT=23173 DPT=54270 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:20:06 kurkobuntu kernel: [55804.164438] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=26880 DF PROTO=TCP SPT=23173 DPT=54270 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:20:43 kurkobuntu kernel: [55841.095900] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=33244 DF PROTO=TCP SPT=23173 DPT=38389 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:20:43 kurkobuntu kernel: [55841.096673] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=33007 DF PROTO=TCP SPT=23173 DPT=38389 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:20:43 kurkobuntu kernel: [55841.097196] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=58275 DF PROTO=TCP SPT=23173 DPT=38389 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:20:43 kurkobuntu kernel: [55841.100227] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=56792 DF PROTO=TCP SPT=23173 DPT=38389 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:20:43 kurkobuntu kernel: [55841.101729] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=30659 DF PROTO=TCP SPT=23173 DPT=38389 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:20:43 kurkobuntu kernel: [55841.110206] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=44279 DF PROTO=TCP SPT=23173 DPT=38389 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:21:04 kurkobuntu kernel: [55862.097151] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=93.158.110.33 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=TCP SPT=80 DPT=51235 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:21:05 kurkobuntu kernel: [55862.315144] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=93.158.110.33 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=TCP SPT=80 DPT=51235 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:21:32 kurkobuntu kernel: [55890.093572] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=93.158.110.33 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=TCP SPT=80 DPT=51235 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:21:54 kurkobuntu kernel: [55912.101195] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=45701 DF PROTO=TCP SPT=23173 DPT=46335 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:22:07 kurkobuntu kernel: [55924.456703] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=98.208.58.113 DST=109.108.2.251 LEN=52 TOS=0x00 PREC=0x00 TTL=41 ID=32923 DF PROTO=TCP SPT=53704 DPT=60060 WINDOW=65535 RES=0x00 ACK URGP=0 
Feb 11 07:22:36 kurkobuntu kernel: [55954.137274] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=10936 DF PROTO=TCP SPT=23173 DPT=43479 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:23:35 kurkobuntu kernel: [56013.103383] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=11975 DF PROTO=TCP SPT=23173 DPT=33092 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:23:35 kurkobuntu kernel: [56013.108210] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=51666 DF PROTO=TCP SPT=23173 DPT=33092 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:23:35 kurkobuntu kernel: [56013.150285] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=43993 DF PROTO=TCP SPT=23173 DPT=33092 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:23:50 kurkobuntu kernel: [56028.106299] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=5609 DF PROTO=TCP SPT=23173 DPT=58743 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:24:01 kurkobuntu ntpd[2530]: kernel time sync status change 2001
Feb 11 07:27:10 kurkobuntu kernel: [56228.057596] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=48399 DF PROTO=TCP SPT=23173 DPT=34267 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:27:10 kurkobuntu kernel: [56228.058292] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=59147 DF PROTO=TCP SPT=23173 DPT=34267 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:27:10 kurkobuntu kernel: [56228.060796] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=46459 DF PROTO=TCP SPT=23173 DPT=34267 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:27:10 kurkobuntu kernel: [56228.062335] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=37436 DF PROTO=TCP SPT=23173 DPT=34267 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:27:10 kurkobuntu kernel: [56228.072467] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=19770 DF PROTO=TCP SPT=23173 DPT=34267 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:27:10 kurkobuntu kernel: [56228.083295] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=15959 DF PROTO=TCP SPT=23173 DPT=34267 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:27:10 kurkobuntu kernel: [56228.086500] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=2116 DF PROTO=TCP SPT=23173 DPT=34267 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:27:10 kurkobuntu kernel: [56228.087971] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=34393 DF PROTO=TCP SPT=23173 DPT=34267 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:27:10 kurkobuntu kernel: [56228.088548] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=10776 DF PROTO=TCP SPT=23173 DPT=34267 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:27:10 kurkobuntu kernel: [56228.089650] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=48923 DF PROTO=TCP SPT=23173 DPT=34267 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:27:36 kurkobuntu kernel: [56254.105099] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=188.222.249.187 DST=109.108.2.251 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=52413 DF PROTO=TCP SPT=23173 DPT=35346 WINDOW=0 RES=0x00 RST URGP=0 
Feb 11 07:27:55 kurkobuntu kernel: [56272.984626] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=125.24.157.175 DST=109.108.2.251 LEN=52 TOS=0x00 PREC=0x00 TTL=93 ID=42408 DF PROTO=TCP SPT=62461 DPT=51717 WINDOW=64095 RES=0x00 ACK URGP=0 
Feb 11 07:30:01 kurkobuntu CRON[9408]: (root) CMD (start -q anacron || :)
Feb 11 07:30:01 kurkobuntu anacron[9411]: Anacron 2.3 started on 2011-02-11
Feb 11 07:30:01 kurkobuntu anacron[9411]: Will run job `cron.daily' in 5 min.
Feb 11 07:30:01 kurkobuntu anacron[9411]: Will run job `cron.weekly' in 10 min.
Feb 11 07:30:01 kurkobuntu anacron[9411]: Will run job `cron.monthly' in 15 min.
Feb 11 07:30:01 kurkobuntu anacron[9411]: Jobs will be executed sequentially
Feb 11 07:35:01 kurkobuntu anacron[9411]: Job `cron.daily' started
Feb 11 07:35:01 kurkobuntu anacron[9424]: Updated timestamp for job `cron.daily' to 2011-02-11
Feb 11 07:39:42 kurkobuntu pulseaudio[2227]: ratelimit.c: 213 events suppressed

```

---

### Post by Cheesehead on 2011-02-11
Here's what I think so far.

1) You have a cron job running hourly at the top of every hour
```
Feb 10 08:00:01 kurkobuntu CRON[16673]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })

```

2) It's not the normal cron.hourly, which runs at 17 minutes past each hour.```
Feb 10 10:17:01 kurkobuntu CRON[20464]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

3) And at 0200, that job is starting a whole lot of network activity, as seen by your firewall:```
Feb 11 02:00:01 kurkobuntu CRON[5150]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Feb 11 02:03:29 kurkobuntu kernel: [36806.510479] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=124.160.133.160 DST=109.108.2.251 LEN=133 TOS=0x00 PREC=0x00 TTL=35 ID=58397 PROTO=UDP SPT=4032 DPT=56260 LEN=113 
Feb 11 02:06:09 kurkobuntu kernel: [36967.156334] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=69.63.181.105 DST=109.108.2.251 LEN=182 TOS=0x00 PREC=0x00 TTL=80 ID=33469 DF PROTO=TCP SPT=5222 DPT=60361 WINDOW=91 RES=0x00 ACK PSH URGP=0 
Feb 11 02:06:36 kurkobuntu kernel: [36993.331525] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=69.63.181.105 DST=109.108.2.251 LEN=182 TOS=0x00 PREC=0x00 TTL=80 ID=33470 DF PROTO=TCP SPT=5222 DPT=60361 WINDOW=91 RES=0x00 ACK PSH URGP=0 
Feb 11 02:07:28 kurkobuntu kernel: [37045.683396] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=69.63.181.105 DST=109.108.2.251 LEN=182 TOS=0x00 PREC=0x00 TTL=80 ID=33471 DF PROTO=TCP SPT=5222 DPT=60361 WINDOW=91 RES=0x00 ACK PSH URGP=0 
Feb 11 02:09:13 kurkobuntu kernel: [37150.384861] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=69.63.181.105 DST=109.108.2.251 LEN=182 TOS=0x00 PREC=0x00 TTL=80 ID=33472 DF PROTO=TCP SPT=5222 DPT=60361 WINDOW=91 RES=0x00 ACK PSH URGP=0 
Feb 11 02:09:48 kurkobuntu kernel: [37186.069412] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=219.108.152.105 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=102 ID=9109 DF PROTO=TCP SPT=60299 DPT=58911 WINDOW=8192 RES=0x00 ACK SYN URGP=0 
Feb 11 02:09:51 kurkobuntu kernel: [37189.073723] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=219.108.152.105 DST=109.108.2.251 LEN=60 TOS=0x00 PREC=0x00 TTL=102 ID=9375 DF PROTO=TCP SPT=60302 DPT=58911 WINDOW=8192 RES=0x00 ACK SYN URGP=0 
Feb 11 02:09:57 kurkobuntu kernel: [37195.083411] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=219.108.152.105 DST=109.108.2.251 LEN=56 TOS=0x00 PREC=0x00 TTL=102 ID=10511 DF PROTO=TCP SPT=60312 DPT=58911 WINDOW=8192 RES=0x00 ACK SYN URGP=0 
Feb 11 02:10:00 kurkobuntu kernel: [37197.508593] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:66:6f:fc:36:00:26:cb:d4:f9:d9:08:00 SRC=173.24.137.238 DST=109.108.2.251 LEN=1500 TOS=0x00 PREC=0x00 TTL=105 ID=18253 DF PROTO=TCP SPT=57238 DPT=60060 WINDOW=63491 RES=0x00 ACK PSH URGP=0 

```


Now, we've looked in the crontab, and it's not there. That's the most common place for a user-created problem.
We've looked in cron.hourly, and it doesn't seem to be there. That's the second most common place for a user-created problem.

Next, let's look in '/etc/cron.d'. Open that folder up and look for any cron job triggering at min=0, hour=*. If in doubt, post those crontabs. /etc/cron.d is the folder that installed packages put their special custom crontabs in -  for example, anacron and php have crontabs within mine. 

Interestingly, this command is specifically looking for tigercron, not regular cron. So let's also look in '/etc/tiger/cronrc'. Same process, look for a command triggering on each hour. This might be part of Tiger's normal checking...take a look at /var/log/tiger for the security logs, and see if there is corresponding tiger activity then.

A couple packages depend on tiger. if you installed harden-tools or checksecurity, then you also installed Tiger.

Let me know what you find!

---

