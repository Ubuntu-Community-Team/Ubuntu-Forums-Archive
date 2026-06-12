---
title: "Mysterious Crashing and CRON?"
date: 2010-02-15
forum: General Help
---

### Post by gagegannon on 2010-02-15
I'm not really sure what's going on here as I'm new to ubuntu. I've searched around for this problem but can't seem to find anything quite like it, (except on google but no one seems to have any answers there). Hopefully someone can help me with what's going on here.
 
First off, I'm running Ubuntu 8.04, (Hardy Heron) on a brand new machine,(Dell VOSTRO 220, barebones) with nothing installed except a LAMP server, (I bought the machine to host a web-site, and that's pretty much all it does). After some difficulity getting apache2 to work, I finally got a test web page up and running. Since that time I've been having some unusual problems with my machine crashing. 
 
I first noticed the problem when I would check my machine late at night. In shaking the mouse to wake up the monitor from sleep mode, I would get no response, just a black screen. When I tried to ssh into it from a different machine, I could not gain access. The only solution would be a hard boot. I could then restart the machine, log in, and everything would be working fine for about 12 hours or so. I would have the same problem repeat it self about every 12 hours or so. I checked the "syslog" log and would see a LOT of messages that seemed to come from my laptop, even when it was turned off. Here is a sample of what I would see:
 
```

Version:1.0 StartHTML:0000000167 EndHTML:0000013819 StartFragment:0000000454 EndFragment:0000013803                                   Feb 13 17:39:01 hal /USR/SBIN/CRON[7233]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)  
 Feb 13 17:43:12 hal ntpd[4624]: synchronized to 91.189.94.4, stratum 2  
 Feb 13 18:05:19 hal -- MARK --  
 Feb 13 18:09:01 hal /USR/SBIN/CRON[7247]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)  
 Feb 13 18:17:01 hal /USR/SBIN/CRON[7258]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)  
 Feb 13 18:39:01 hal /USR/SBIN/CRON[7265]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)  
 Feb 13 18:41:48 hal ntpd[4624]: synchronized to 132.246.168.164, stratum 2  
 Feb 13 19:05:19 hal -- MARK --  
 Feb 13 19:09:01 hal /USR/SBIN/CRON[7281]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)  
 Feb 13 19:17:01 hal /USR/SBIN/CRON[7292]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)  
 Feb 13 19:31:50 hal kernel: [ 3197.418648] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=57124 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:32:21 hal kernel: [ 3200.849413] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=36980 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:32:53 hal kernel: [ 3204.331493] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=20739 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:33:24 hal kernel: [ 3207.883316] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=16196 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:33:55 hal kernel: [ 3211.263574] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=14104 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:34:25 hal kernel: [ 3214.642190] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=15732 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:34:56 hal kernel: [ 3218.096922] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=42152 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:35:28 hal kernel: [ 3221.601835] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=57839 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:35:58 hal kernel: [ 3225.017516] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=8133 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:36:30 hal kernel: [ 3228.834353] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=45534 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:37:00 hal kernel: [ 3232.225552] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=53457 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:37:31 hal kernel: [ 3235.677379] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=27008 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:39:01 hal /USR/SBIN/CRON[7298]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)  
 Feb 13 19:40:33 hal kernel: [ 3255.621552] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=11556 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:41:04 hal kernel: [ 3259.062270] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=16179 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:41:35 hal kernel: [ 3262.518910] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=25700 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:42:06 hal kernel: [ 3265.944836] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=29697 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:42:37 hal kernel: [ 3269.462755] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=13418 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:43:08 hal kernel: [ 3272.908869] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=36925 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:43:39 hal kernel: [ 3276.340715] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=7617 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:44:10 hal kernel: [ 3279.742987] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=20219 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:44:41 hal kernel: [ 3283.167136] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=8398 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:45:12 hal kernel: [ 3286.671159] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=31160 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:45:43 hal kernel: [ 3290.093177] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=34046 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:46:14 hal kernel: [ 3293.615300] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=968 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:46:45 hal kernel: [ 3297.099855] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=53322 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:47:16 hal kernel: [ 3300.527092] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=33822 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:47:47 hal kernel: [ 3303.963133] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=30317 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:48:18 hal kernel: [ 3307.449679] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=33363 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:48:49 hal kernel: [ 3310.844685] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=38009 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:49:20 hal kernel: [ 3314.352377] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=39767 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:49:51 hal kernel: [ 3317.814552] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=55231 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:50:22 hal kernel: [ 3321.260688] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=35745 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:50:53 hal kernel: [ 3324.717882] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=64741 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:51:24 hal kernel: [ 3328.133718] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=15841 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:51:55 hal kernel: [ 3331.603784] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=46739 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:52:26 hal kernel: [ 3335.080510] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=7613 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:52:57 hal kernel: [ 3338.552323] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=7520 PROTO=UDP SPT=631 DPT=631 LEN=174  
 Feb 13 19:53:08 hal kernel: [ 3339.795793] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:e3:d5:3c:9f:08:00 SRC=192.168.1.70 DST=192.168.1.255 LEN=196 TOS=0x00 PREC=0x00 TTL=64 ID=3879 PROTO=UDP SPT=631 DPT=631 LEN=176  
 Feb 13 20:05:19 hal -- MARK --  
 Feb 13 20:09:01 hal /USR/SBIN/CRON[7312]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)  
 Feb 13 20:17:01 hal /USR/SBIN/CRON[7323]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)  
 Feb 13 20:39:01 hal /USR/SBIN/CRON[7330]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)  
 Feb 13 21:05:19 hal -- MARK --  
 Feb 13 21:09:01 hal /USR/SBIN/CRON[7344]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)  
 Feb 13 21:17:01 hal /USR/SBIN/CRON[7355]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)  
 
```
As I work during the day, I decided to shut down my machine and figure it out at a later time, (this was Friday past, 13-Feb-10). As I was about to leave for work this morning, (15-Feb-10) I thought I'd turn my machine back on and let it run for the day. When I did, I got a flashing Amber light and repetitive beeps, needles to say the machine would not start. When I returned home, I opened up the machine, swapped the two sticks of RAM around, and restarted the machine flawlessly. Both sticks of RAM were firmly seated and not loose? Before doing this, I disconnected the box from the internet and it is still unconnected.
 
I checked my message log again after restart and I see that a process is till running:
 
```

Version:1.0 StartHTML:0000000167 EndHTML:0000089636 StartFragment:0000000454 EndFragment:0000089620                                   Feb 15 16:47:10 hal syslogd 1.5.0#1ubuntu1: restart.  
 Feb 15 16:47:11 hal kernel: Inspecting /boot/System.map-2.6.24-27-server  
 Feb 15 16:47:11 hal kernel: Loaded 28791 symbols from /boot/System.map-2.6.24-27-server.  
 Feb 15 16:47:11 hal kernel: Symbols match kernel version 2.6.24.  
 Feb 15 16:47:11 hal kernel: Loaded 18141 symbols from 96 modules.  
 Feb 15 16:47:11 hal kernel: [    0.000000] Initializing cgroup subsys cpuset  
 Feb 15 16:47:11 hal kernel: [    0.000000] Initializing cgroup subsys cpu  
 Feb 15 16:47:11 hal kernel: [    0.000000] Linux version 2.6.24-27-server (buildd@vernadsky) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Thu Jan 28 00:36:19 UTC 2010 (Ubuntu 2.6.24-27.65-server)  
 Feb 15 16:47:11 hal kernel: [    0.000000] BIOS-provided physical RAM map:  
 Feb 15 16:47:11 hal kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)  
 Feb 15 16:47:11 hal kernel: [    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)  
 Feb 15 16:47:11 hal kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)  
 Feb 15 16:47:11 hal kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007dd60000 (usable)  
 Feb 15 16:47:11 hal kernel: [    0.000000]  BIOS-e820: 000000007dd60000 - 000000007dd6e000 (ACPI data) 
 Feb 15 16:47:11 hal kernel: [    0.000000]  BIOS-e820: 000000007dd6e000 - 000000007ddb8000 (ACPI NVS)  
 Feb 15 16:47:11 hal kernel: [    0.000000]  BIOS-e820: 000000007ddbc000 - 0000000080000000 (reserved)  
 Feb 15 16:47:11 hal kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)  
 Feb 15 16:47:11 hal kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)  
 Feb 15 16:47:11 hal kernel: [    0.000000] 1117MB HIGHMEM available.  
 Feb 15 16:47:11 hal kernel: [    0.000000] 896MB LOWMEM available.  
 Feb 15 16:47:11 hal kernel: [    0.000000] found SMP MP-table at 000ff780  
 Feb 15 16:47:11 hal kernel: [    0.000000] NX (Execute Disable) protection: active  
 Feb 15 16:47:11 hal kernel: [    0.000000] Entering add_active_range(0, 0, 515424) 0 entries of 256 used  
 Feb 15 16:47:11 hal kernel: [    0.000000] Zone PFN ranges:  
 Feb 15 16:47:11 hal kernel: [    0.000000]   DMA             0 ->     4096  
 Feb 15 16:47:11 hal kernel: [    0.000000]   Normal       4096 ->   229376  
 Feb 15 16:47:11 hal kernel: [    0.000000]   HighMem    229376 ->   515424  
 Feb 15 16:47:11 hal kernel: [    0.000000] Movable zone start PFN for each node  
 Feb 15 16:47:11 hal kernel: [    0.000000] early_node_map[1] active PFN ranges  
 Feb 15 16:47:11 hal kernel: [    0.000000]     0:        0 ->   515424  
 Feb 15 16:47:11 hal kernel: [    0.000000] On node 0 totalpages: 515424  
 Feb 15 16:47:11 hal kernel: [    0.000000]   DMA zone: 32 pages used for memmap  
 Feb 15 16:47:11 hal kernel: [    0.000000]   DMA zone: 0 pages reserved  
 Feb 15 16:47:11 hal kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0  
 Feb 15 16:47:11 hal kernel: [    0.000000]   Normal zone: 1760 pages used for memmap  
 Feb 15 16:47:11 hal kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31  
 Feb 15 16:47:11 hal kernel: [    0.000000]   HighMem zone: 2234 pages used for memmap  
 Feb 15 16:47:11 hal kernel: [    0.000000]   HighMem zone: 283814 pages, LIFO batch:31  
 Feb 15 16:47:11 hal kernel: [    0.000000]   Movable zone: 0 pages used for memmap  
 Feb 15 16:47:11 hal kernel: [    0.000000] DMI present.  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F9EE0 checksum 0  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: RSDP 000F9EE0, 0014 (r0 ACPIAM)  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: RSDT 7DD60000, 0044 (r1 DELL    FX09    20081024 MSFT       97)  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: FACP 7DD60200, 0084 (r1 102408 FACP1017 20081024 MSFT       97)  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI Warning (tbfadt-0442): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000814/0 [20070126]  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: DSDT 7DD605C0, 6E47 (r1  7C4D1 7C4D1P29       21 INTL 20051117)  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: FACS 7DD6E000, 0040  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: APIC 7DD60390, 006C (r1 102408 APIC1017 20081024 MSFT       97)  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: MCFG 7DD60400, 003C (r1 102408 OEMMCFG  20081024 MSFT       97)  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: SLIC 7DD60440, 0176 (r1 DELL    FX09    20081024 MSFT       97)  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: OEMB 7DD6E040, 0072 (r1 102408 OEMB1017 20081024 MSFT       97)  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: HPET 7DD685C0, 0038 (r1 102408 OEMHPET  20081024 MSFT       97)  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: GSCI 7DD6E0C0, 2024 (r1 102408 GMCHSCI  20081024 MSFT       97)  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: SSDT 7DD70B40, 0A7C (r1 DpgPmm    CpuPm       12 INTL 20051117)  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: Local APIC address 0xfee00000  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)  
 Feb 15 16:47:11 hal kernel: [    0.000000] Processor #0 7:7 APIC version 20  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)  
 Feb 15 16:47:11 hal kernel: [    0.000000] Processor #1 7:7 APIC version 20  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])  
 Feb 15 16:47:11 hal kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level) 
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: IRQ0 used by override.  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: IRQ2 used by override.  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: IRQ9 used by override.  
 Feb 15 16:47:11 hal kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs  
 Feb 15 16:47:11 hal kernel: [    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000  
 Feb 15 16:47:11 hal kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information  
 Feb 15 16:47:11 hal kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000)  
 Feb 15 16:47:11 hal kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 000000000009f000  
 Feb 15 16:47:11 hal kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000  
 Feb 15 16:47:11 hal kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000  
 Feb 15 16:47:11 hal kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000  
 Feb 15 16:47:11 hal kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 511398  
 Feb 15 16:47:11 hal kernel: [    0.000000] Kernel command line: root=/dev/mapper/hal-root ro quiet splash  
 Feb 15 16:47:11 hal kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)  
 Feb 15 16:47:11 hal kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)  
 Feb 15 16:47:11 hal kernel: [    0.000000] Enabling fast FPU save and restore... done.  
 Feb 15 16:47:11 hal kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.  
 Feb 15 16:47:11 hal kernel: [    0.000000] Initializing CPU#0  
 Feb 15 16:47:11 hal kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)  
 Feb 15 16:47:11 hal kernel: [    0.000000] Detected 2493.804 MHz processor.  
 Feb 15 16:47:11 hal kernel: [   16.088208] Console: colour VGA+ 80x25  
 Feb 15 16:47:11 hal kernel: [   16.088210] console [tty0] enabled  
 Feb 15 16:47:11 hal kernel: [   16.088423] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)  
 Feb 15 16:47:11 hal kernel: [   16.088632] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)  
 Feb 15 16:47:11 hal kernel: [   16.148521] Memory: 2030916k/2061696k available (2261k kernel code, 29480k reserved, 1042k data, 384k init, 1144192k highmem)  
 Feb 15 16:47:11 hal kernel: [   16.148526] virtual kernel memory layout:  
 Feb 15 16:47:11 hal kernel: [   16.148526]     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)  
 Feb 15 16:47:11 hal kernel: [   16.148527]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)  
 Feb 15 16:47:11 hal kernel: [   16.148528]     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)  
 Feb 15 16:47:11 hal kernel: [   16.148529]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)  
 Feb 15 16:47:11 hal kernel: [   16.148529]       .init : 0xc0440000 - 0xc04a0000   ( 384 kB)  
 Feb 15 16:47:11 hal kernel: [   16.148530]       .data : 0xc033565b - 0xc0439fe4   (1042 kB)  
 Feb 15 16:47:11 hal kernel: [   16.148531]       .text : 0xc0100000 - 0xc033565b   (2261 kB)  
 Feb 15 16:47:11 hal kernel: [   16.148533] Checking if this processor honours the WP bit even in supervisor mode... Ok.  
 Feb 15 16:47:11 hal kernel: [   16.148565] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1  
 Feb 15 16:47:11 hal kernel: [   16.148669] hpet clockevent registered  
 Feb 15 16:47:11 hal kernel: [   16.148675] Calibrating delay loop (skipped), using tsc calculated value.. 4987.60 BogoMIPS (lpj=24938040)  
 Feb 15 16:47:11 hal kernel: [   16.148692] Security Framework initialized  
 Feb 15 16:47:11 hal kernel: [   16.148697] SELinux:  Disabled at boot.  
 Feb 15 16:47:11 hal kernel: [   16.148708] AppArmor: AppArmor initialized  
 Feb 15 16:47:11 hal kernel: [   16.148711] Failure registering capabilities with primary security module.  
 Feb 15 16:47:11 hal kernel: [   16.148717] Mount-cache hash table entries: 512  
 Feb 15 16:47:11 hal kernel: [   16.148811] Initializing cgroup subsys ns  
 Feb 15 16:47:11 hal kernel: [   16.148816] Initializing cgroup subsys cpuacct  
 Feb 15 16:47:11 hal kernel: [   16.148824] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000  
 Feb 15 16:47:11 hal kernel: [   16.148828] monitor/mwait feature present.  
 Feb 15 16:47:11 hal kernel: [   16.148830] using mwait in idle threads.  
 Feb 15 16:47:11 hal kernel: [   16.148833] CPU: L1 I cache: 32K, L1 D cache: 32K  
 Feb 15 16:47:11 hal kernel: [   16.148834] CPU: L2 cache: 2048K  
 Feb 15 16:47:11 hal kernel: [   16.148836] CPU: Physical Processor ID: 0  
 Feb 15 16:47:11 hal kernel: [   16.148837] CPU: Processor Core ID: 0  
 Feb 15 16:47:11 hal kernel: [   16.148839] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000  
 Feb 15 16:47:11 hal kernel: [   16.148845] Compat vDSO mapped to ffffe000.  
 Feb 15 16:47:11 hal kernel: [   16.148855] Checking 'hlt' instruction... OK.  
 Feb 15 16:47:11 hal kernel: [   16.188991] SMP alternatives: switching to UP code  
 Feb 15 16:47:11 hal kernel: [   16.190251] Early unpacking initramfs... done  
 Feb 15 16:47:11 hal kernel: [   16.450238] ACPI: Core revision 20070126  
 Feb 15 16:47:11 hal kernel: [   16.450277] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.  
 Feb 15 16:47:11 hal kernel: [   16.474745] CPU0: Intel Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz stepping 06  
 Feb 15 16:47:11 hal kernel: [   16.474757] SMP alternatives: switching to SMP code  
 Feb 15 16:47:11 hal kernel: [   16.475375] Booting processor 1/1 eip 3000  
 Feb 15 16:47:11 hal kernel: [   16.485607] Initializing CPU#1  
 Feb 15 16:47:11 hal kernel: [   16.627934] Calibrating delay using timer specific routine.. 4987.48 BogoMIPS (lpj=24937427)  
 Feb 15 16:47:11 hal kernel: [   16.627939] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000  
 Feb 15 16:47:11 hal kernel: [   16.627943] monitor/mwait feature present.  
 Feb 15 16:47:11 hal kernel: [   16.627945] CPU: L1 I cache: 32K, L1 D cache: 32K  
 Feb 15 16:47:11 hal kernel: [   16.627946] CPU: L2 cache: 2048K  
 Feb 15 16:47:11 hal kernel: [   16.627948] CPU: Physical Processor ID: 0  
 Feb 15 16:47:11 hal kernel: [   16.627948] CPU: Processor Core ID: 1  
 Feb 15 16:47:11 hal kernel: [   16.627950] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000  
 Feb 15 16:47:11 hal kernel: [   16.628460] CPU1: Intel Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz stepping 06  
 Feb 15 16:47:11 hal kernel: [   16.628475] Total of 2 processors activated (9975.09 BogoMIPS).  
 Feb 15 16:47:11 hal kernel: [   16.628616] ENABLING IO-APIC IRQs  
 Feb 15 16:47:11 hal kernel: [   16.628777] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1  
 Feb 15 16:47:11 hal kernel: [   16.847677] checking TSC synchronization [CPU#0 -> CPU#1]: passed.  
 Feb 15 16:47:11 hal kernel: [   16.867658] Brought up 2 CPUs  
 Feb 15 16:47:11 hal kernel: [   16.867674] CPU0 attaching sched-domain:  
 Feb 15 16:47:11 hal kernel: [   16.867676]  domain 0: span 03  
 Feb 15 16:47:11 hal kernel: [   16.867677]   groups: 01 02  
 Feb 15 16:47:11 hal kernel: [   16.867679] CPU1 attaching sched-domain:  
 Feb 15 16:47:11 hal kernel: [   16.867680]  domain 0: span 03  
 Feb 15 16:47:11 hal kernel: [   16.867681]   groups: 02 01  
 Feb 15 16:47:11 hal kernel: [   16.867832] net_namespace: 64 bytes  
 Feb 15 16:47:11 hal kernel: [   16.867839] Booting paravirtualized kernel on bare hardware  
 Feb 15 16:47:11 hal kernel: [   16.868151] Time: 21:46:27  Date: 02/15/10  
 Feb 15 16:47:11 hal kernel: [   16.868172] NET: Registered protocol family 16  
 Feb 15 16:47:11 hal kernel: [   16.868297] EISA bus registered  
 Feb 15 16:47:11 hal kernel: [   16.868301] ACPI: bus type pci registered  
 Feb 15 16:47:11 hal kernel: [   16.868452] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3  
 Feb 15 16:47:11 hal kernel: [   16.868453] PCI: Using configuration type 1  
 Feb 15 16:47:11 hal kernel: [   16.868462] Setting up standard PCI resources  
 Feb 15 16:47:11 hal kernel: [   16.871676] ACPI: EC: Look up EC in DSDT  
 Feb 15 16:47:11 hal kernel: [   16.875991] ACPI: Interpreter enabled  
 Feb 15 16:47:11 hal kernel: [   16.875993] ACPI: (supports S0 S1 S3 S4 S5)  
 Feb 15 16:47:11 hal kernel: [   16.876003] ACPI: Using IOAPIC for interrupt routing  
 Feb 15 16:47:11 hal kernel: [   16.876136] Error attaching device data  
 Feb 15 16:47:11 hal kernel: [   16.876163] Error attaching device data  
 Feb 15 16:47:11 hal kernel: [   16.876191] Error attaching device data  
 Feb 15 16:47:11 hal kernel: [   16.876216] Error attaching device data  
 Feb 15 16:47:11 hal kernel: [   16.883003] ACPI: PCI Root Bridge [PCI0] (0000:00)  
 Feb 15 16:47:11 hal kernel: [   16.884025] PCI: Transparent bridge - 0000:00:1e.0  
 Feb 15 16:47:11 hal kernel: [   16.884048] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]  
 Feb 15 16:47:11 hal kernel: [   16.884166] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]  
 Feb 15 16:47:11 hal kernel: [   16.884276] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]  
 Feb 15 16:47:11 hal kernel: [   16.884345] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]  
 Feb 15 16:47:11 hal kernel: [   16.897282] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12 14 15)  
 Feb 15 16:47:11 hal kernel: [   16.897380] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)  
 Feb 15 16:47:11 hal kernel: [   16.897476] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 *10 11 12 14 15)  
 Feb 15 16:47:11 hal kernel: [   16.897596] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12 14 *15)  
 Feb 15 16:47:11 hal kernel: [   16.897692] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.  
 Feb 15 16:47:11 hal kernel: [   16.897789] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 *14 15)  
 Feb 15 16:47:11 hal kernel: [   16.897885] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 7 10 11 12 14 15)  
 Feb 15 16:47:11 hal kernel: [   16.897981] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 *7 10 11 12 14 15)  
 Feb 15 16:47:11 hal kernel: [   16.898089] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  15, should be 14 [20070126]  
 Feb 15 16:47:11 hal kernel: [   16.898100] Linux Plug and Play Support v0.97 (c) Adam Belay  
 Feb 15 16:47:11 hal kernel: [   16.898119] pnp: PnP ACPI init  
 Feb 15 16:47:11 hal kernel: [   16.898124] ACPI: bus type pnp registered  
 Feb 15 16:47:11 hal kernel: [   16.901490] pnp: PnP ACPI: found 15 devices  
 Feb 15 16:47:11 hal kernel: [   16.901492] ACPI: ACPI bus type pnp unregistered  
 Feb 15 16:47:11 hal kernel: [   16.901494] PnPBIOS: Disabled by ACPI PNP  
 Feb 15 16:47:11 hal kernel: [   16.901632] PCI: Using ACPI for IRQ routing  
 Feb 15 16:47:11 hal kernel: [   16.901634] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report  
 Feb 15 16:47:11 hal kernel: [   16.957580] NET: Registered protocol family 8  
 Feb 15 16:47:11 hal kernel: [   16.957581] NET: Registered protocol family 20  
 Feb 15 16:47:11 hal kernel: [   16.957600] NetLabel: Initializing  
 Feb 15 16:47:11 hal kernel: [   16.957601] NetLabel:  domain hash size = 128  
 Feb 15 16:47:11 hal kernel: [   16.957602] NetLabel:  protocols = UNLABELED CIPSOv4  
 Feb 15 16:47:11 hal kernel: [   16.957609] NetLabel:  unlabeled traffic allowed by default  
 Feb 15 16:47:11 hal kernel: [   16.957614] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0  
 Feb 15 16:47:11 hal kernel: [   16.957617] hpet0: 4 64-bit timers, 14318180 Hz  
 Feb 15 16:47:11 hal kernel: [   16.958641] AppArmor: AppArmor Filesystem Enabled  
 Feb 15 16:47:11 hal kernel: [   16.967421] Time: tsc clocksource has been installed.  
 Feb 15 16:47:11 hal kernel: [   16.967430] Switched to high resolution mode on CPU 0  
 Feb 15 16:47:11 hal kernel: [   16.967507] Switched to high resolution mode on CPU 1  
 Feb 15 16:47:11 hal kernel: [   17.017396] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved  
 Feb 15 16:47:11 hal kernel: [   17.017400] system 00:01: iomem range 0xfed90000-0xfed93fff has been reserved  
 Feb 15 16:47:11 hal kernel: [   17.017412] system 00:07: ioport range 0x290-0x29f has been reserved  
 Feb 15 16:47:11 hal kernel: [   17.017415] system 00:07: ioport range 0x290-0x29f has been reserved  
 Feb 15 16:47:11 hal kernel: [   17.017419] system 00:07: ioport range 0xa20-0xa2f has been reserved  
 Feb 15 16:47:11 hal kernel: [   17.017422] system 00:07: ioport range 0xa30-0xa3f has been reserved  
 Feb 15 16:47:11 hal kernel: [   17.017432] system 00:08: ioport range 0x4c0-0x4ff has been reserved  
 Feb 15 16:47:11 hal kernel: [   17.017434] system 00:08: ioport range 0x800-0x87f has been reserved  
 Feb 15 16:47:11 hal kernel: [   17.017435] system 00:08: ioport range 0x480-0x4bf has been reserved  
 Feb 15 16:47:11 hal kernel: [   17.017437] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved  
 Feb 15 16:47:11 hal kernel: [   17.017439] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved  
 Feb 15 16:47:11 hal kernel: [   17.017441] system 00:08: iomem range 0xfed40000-0xfed8ffff has been reserved  
 Feb 15 16:47:11 hal kernel: [   17.017445] system 00:0b: iomem range 0xffc00000-0xffefffff could not be reserved  
 Feb 15 16:47:11 hal kernel: [   17.017448] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved  
 Feb 15 16:47:11 hal kernel: [   17.017450] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved  
 Feb 15 16:47:11 hal kernel: [   17.017454] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved  
 Feb 15 16:47:11 hal kernel: [   17.017458] system 00:0e: iomem range 0x0-0x9ffff could not be reserved  
 Feb 15 16:47:11 hal kernel: [   17.017459] system 00:0e: iomem range 0xc0000-0xcffff could not be reserved  
 Feb 15 16:47:11 hal kernel: [   17.017461] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved  
 Feb 15 16:47:11 hal kernel: [   17.017463] system 00:0e: iomem range 0x100000-0x7ddfffff could not be reserved  
 Feb 15 16:47:11 hal kernel: [   17.017465] system 00:0e: iomem range 0x0-0x0 could not be reserved  
 Feb 15 16:47:11 hal kernel: [   17.047684] PCI: Bridge: 0000:00:1c.0  
 Feb 15 16:47:11 hal kernel: [   17.047686]   IO window: disabled.  
 Feb 15 16:47:11 hal kernel: [   17.047689]   MEM window: disabled.  
 Feb 15 16:47:11 hal kernel: [   17.047692]   PREFETCH window: disabled.  
 Feb 15 16:47:11 hal kernel: [   17.047695] PCI: Bridge: 0000:00:1c.2  
 Feb 15 16:47:11 hal kernel: [   17.047697]   IO window: e000-efff  
 Feb 15 16:47:11 hal kernel: [   17.047700]   MEM window: feb00000-febfffff  
 Feb 15 16:47:11 hal kernel: [   17.047703]   PREFETCH window: fdf00000-fdffffff  
 Feb 15 16:47:11 hal kernel: [   17.047707] PCI: Bridge: 0000:00:1e.0  
 Feb 15 16:47:11 hal kernel: [   17.047707]   IO window: disabled.  
 Feb 15 16:47:11 hal kernel: [   17.047711]   MEM window: disabled.  
 Feb 15 16:47:11 hal kernel: [   17.047713]   PREFETCH window: disabled.  
 Feb 15 16:47:11 hal kernel: [   17.047732] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16  
 Feb 15 16:47:11 hal kernel: [   17.047736] PCI: Setting latency timer of device 0000:00:1c.0 to 64  
 Feb 15 16:47:11 hal kernel: [   17.047750] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 17  
 Feb 15 16:47:11 hal kernel: [   17.047754] PCI: Setting latency timer of device 0000:00:1c.2 to 64  
 Feb 15 16:47:11 hal kernel: [   17.047762] PCI: Setting latency timer of device 0000:00:1e.0 to 64  
 Feb 15 16:47:11 hal kernel: [   17.047770] NET: Registered protocol family 2  
 Feb 15 16:47:11 hal kernel: [   17.147221] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)  
 Feb 15 16:47:11 hal kernel: [   17.147379] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)  
 Feb 15 16:47:11 hal kernel: [   17.147705] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)  
 Feb 15 16:47:11 hal kernel: [   17.147881] TCP: Hash tables configured (established 131072 bind 65536)  
 Feb 15 16:47:11 hal kernel: [   17.147883] TCP reno registered  
 Feb 15 16:47:11 hal kernel: [   17.177240] checking if image is initramfs... it is  
 Feb 15 16:47:11 hal kernel: [   17.689841] Freeing initrd memory: 8183k freed  
 Feb 15 16:47:11 hal kernel: [   17.690366] audit: initializing netlink socket (disabled)  
 Feb 15 16:47:11 hal kernel: [   17.690377] audit(1266270387.402:1): initialized  
 Feb 15 16:47:11 hal kernel: [   17.690598] highmem bounce pool size: 64 pages  
 Feb 15 16:47:11 hal kernel: [   17.690600] Total HugeTLB memory allocated, 0  
 Feb 15 16:47:11 hal kernel: [   17.691869] VFS: Disk quotas dquot_6.5.1  
 Feb 15 16:47:11 hal kernel: [   17.691916] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
 Feb 15 16:47:11 hal kernel: [   17.692042] io scheduler noop registered  
 Feb 15 16:47:11 hal kernel: [   17.692043] io scheduler anticipatory registered  
 Feb 15 16:47:11 hal kernel: [   17.692045] io scheduler deadline registered (default)  
 Feb 15 16:47:11 hal kernel: [   17.692052] io scheduler cfq registered  
 Feb 15 16:47:11 hal kernel: [   17.692061] Boot video device is 0000:00:02.0  
 Feb 15 16:47:11 hal kernel: [   17.692224] PCI: Setting latency timer of device 0000:00:1c.0 to 64  
 Feb 15 16:47:11 hal kernel: [   17.692257] assign_interrupt_mode Found MSI capability  
 Feb 15 16:47:11 hal kernel: [   17.692288] Allocate Port Service[0000:00:1c.0:pcie00]  
 Feb 15 16:47:11 hal kernel: [   17.692309] Allocate Port Service[0000:00:1c.0:pcie02]  
 Feb 15 16:47:11 hal kernel: [   17.692369] PCI: Setting latency timer of device 0000:00:1c.2 to 64  
 Feb 15 16:47:11 hal kernel: [   17.692402] assign_interrupt_mode Found MSI capability  
 Feb 15 16:47:11 hal kernel: [   17.692428] Allocate Port Service[0000:00:1c.2:pcie00]  
 Feb 15 16:47:11 hal kernel: [   17.692449] Allocate Port Service[0000:00:1c.2:pcie02]  
 Feb 15 16:47:11 hal kernel: [   17.692609] isapnp: Scanning for PnP cards...  
 Feb 15 16:47:11 hal kernel: [   18.048554] isapnp: No Plug & Play device found  
 Feb 15 16:47:11 hal kernel: [   18.064655] Real Time Clock Driver v1.12ac  
 Feb 15 16:47:11 hal kernel: [   18.064790] hpet_resources: 0xfed00000 is busy  
 Feb 15 16:47:11 hal kernel: [   18.064828] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled  
 Feb 15 16:47:11 hal kernel: [   18.064932] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A  
 Feb 15 16:47:11 hal kernel: [   18.065377] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A  
 Feb 15 16:47:11 hal kernel: [   18.065898] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize  
 Feb 15 16:47:11 hal kernel: [   18.065945] input: Macintosh mouse button emulation as /devices/virtual/input/input0  
 Feb 15 16:47:11 hal kernel: [   18.066036] PNP: No PS/2 controller found. Probing ports directly.  
 Feb 15 16:47:11 hal kernel: [   18.066334] serio: i8042 KBD port at 0x60,0x64 irq 1  
 Feb 15 16:47:11 hal kernel: [   18.066339] serio: i8042 AUX port at 0x60,0x64 irq 12  
 Feb 15 16:47:11 hal kernel: [   18.115770] mice: PS/2 mouse device common for all mice  
 Feb 15 16:47:11 hal kernel: [   18.115840] EISA: Probing bus 0 at eisa.0  
 Feb 15 16:47:11 hal kernel: [   18.115865] EISA: Detected 0 cards.  
 Feb 15 16:47:11 hal kernel: [   18.115867] cpuidle: using governor ladder  
 Feb 15 16:47:11 hal kernel: [   18.115868] cpuidle: using governor menu  
 Feb 15 16:47:11 hal kernel: [   18.115929] NET: Registered protocol family 1  
 Feb 15 16:47:11 hal kernel: [   18.115948] Using IPI No-Shortcut mode  
 Feb 15 16:47:11 hal kernel: [   18.115971] registered taskstats version 1  
 Feb 15 16:47:11 hal kernel: [   18.116040]   Magic number: 14:565:803  
 Feb 15 16:47:11 hal kernel: [   18.116091] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found  
 Feb 15 16:47:11 hal kernel: [   18.116358] Freeing unused kernel memory: 384k freed  
 Feb 15 16:47:11 hal kernel: [   18.116388] Write protecting the kernel read-only data: 829k  
 Feb 15 16:47:11 hal kernel: [   19.265140] fuse init (API version 7.9)  
 Feb 15 16:47:11 hal kernel: [   19.278987] ACPI: SSDT 7DD700F0, 0277 (r1 DpgPmm  P001Ist       11 INTL 20051117)  
 Feb 15 16:47:11 hal kernel: [   19.279147] ACPI: SSDT 7DD705F0, 04B2 (r1  PmRef  P001Cst     3001 INTL 20051117)  
 Feb 15 16:47:11 hal kernel: [   19.279372] Monitor-Mwait will be used to enter C-1 state  
 Feb 15 16:47:11 hal kernel: [   19.279374] Monitor-Mwait will be used to enter C-2 state  
 Feb 15 16:47:11 hal kernel: [   19.279376] Monitor-Mwait will be used to enter C-3 state  
 Feb 15 16:47:11 hal kernel: [   19.279452] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])  
 Feb 15 16:47:11 hal kernel: [   19.279616] ACPI: SSDT 7DD70370, 0277 (r1 DpgPmm  P002Ist       12 INTL 20051117)  
 Feb 15 16:47:11 hal kernel: [   19.279775] ACPI: SSDT 7DD70AB0, 0085 (r1  PmRef  P002Cst     3000 INTL 20051117)  
 Feb 15 16:47:11 hal kernel: [   19.280066] Marking TSC unstable due to: TSC halts in idle.  
 Feb 15 16:47:11 hal kernel: [   19.280123] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])  
 Feb 15 16:47:11 hal kernel: [   19.280134] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]  
 Feb 15 16:47:11 hal kernel: [   19.280141] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]  
 Feb 15 16:47:11 hal kernel: [   19.283916] Time: hpet clocksource has been installed.  
 Feb 15 16:47:11 hal kernel: [   19.290961] device-mapper: uevent: version 1.0.3  
 Feb 15 16:47:11 hal kernel: [   19.291016] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com  
 Feb 15 16:47:11 hal kernel: [   19.470296] usbcore: registered new interface driver usbfs  
 Feb 15 16:47:11 hal kernel: [   19.470316] usbcore: registered new interface driver hub  
 Feb 15 16:47:11 hal kernel: [   19.470872] usbcore: registered new device driver usb  
 Feb 15 16:47:11 hal kernel: [   19.478034] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 17  
 Feb 15 16:47:11 hal kernel: [   19.478046] PCI: Setting latency timer of device 0000:00:1a.7 to 64  
 Feb 15 16:47:11 hal kernel: [   19.478049] ehci_hcd 0000:00:1a.7: EHCI Host Controller  
 Feb 15 16:47:11 hal kernel: [   19.478235] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1  
 Feb 15 16:47:11 hal kernel: [   19.482136] ehci_hcd 0000:00:1a.7: debug port 1  
 Feb 15 16:47:11 hal kernel: [   19.482141] PCI: cache line size of 32 is not supported by device 0000:00:1a.7  
 Feb 15 16:47:11 hal kernel: [   19.482149] ehci_hcd 0000:00:1a.7: irq 17, io mem 0xfeafbc00  
 Feb 15 16:47:11 hal kernel: [   19.487006] USB Universal Host Controller Interface driver v3.0  
 Feb 15 16:47:11 hal kernel: [   19.506071] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004  
 Feb 15 16:47:11 hal kernel: [   19.506174] usb usb1: configuration #1 chosen from 1 choice  
 Feb 15 16:47:11 hal kernel: [   19.506191] hub 1-0:1.0: USB hub found  
 Feb 15 16:47:11 hal kernel: [   19.506195] hub 1-0:1.0: 6 ports detected  
 Feb 15 16:47:11 hal kernel: [   19.516916] SCSI subsystem initialized  
 Feb 15 16:47:11 hal kernel: [   19.524092] libata version 3.00 loaded.  
 Feb 15 16:47:11 hal kernel: [   19.616000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18  
 Feb 15 16:47:11 hal kernel: [   19.616014] PCI: Setting latency timer of device 0000:00:1d.7 to 64  
 Feb 15 16:47:11 hal kernel: [   19.616017] ehci_hcd 0000:00:1d.7: EHCI Host Controller  
 Feb 15 16:47:11 hal kernel: [   19.616034] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2  
 Feb 15 16:47:11 hal kernel: [   19.619920] ehci_hcd 0000:00:1d.7: debug port 1  
 Feb 15 16:47:11 hal kernel: [   19.619925] PCI: cache line size of 32 is not supported by device 0000:00:1d.7  
 Feb 15 16:47:11 hal kernel: [   19.619932] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xfeafb800  
 Feb 15 16:47:11 hal kernel: [   19.643370] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004  
 Feb 15 16:47:11 hal kernel: [   19.643451] usb usb2: configuration #1 chosen from 1 choice  
 Feb 15 16:47:11 hal kernel: [   19.643467] hub 2-0:1.0: USB hub found  
 Feb 15 16:47:11 hal kernel: [   19.643471] hub 2-0:1.0: 6 ports detected  
 Feb 15 16:47:11 hal kernel: [   19.753274] r8169 Gigabit Ethernet driver 2.2LK loaded  
 Feb 15 16:47:11 hal kernel: [   19.753316] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 17  
 Feb 15 16:47:11 hal kernel: [   19.753349] PCI: Setting latency timer of device 0000:02:00.0 to 64  
 Feb 15 16:47:11 hal kernel: [   19.753606] eth0: RTL8168c/8111c at 0xf8834000, 00:21:9b:27:d2:71, XID 3c4000c0 IRQ 221  
 Feb 15 16:47:11 hal kernel: [   19.753683] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 19  
 Feb 15 16:47:11 hal kernel: [   19.753689] PCI: Setting latency timer of device 0000:00:1a.0 to 64  
 Feb 15 16:47:11 hal kernel: [   19.753691] uhci_hcd 0000:00:1a.0: UHCI Host Controller  
 Feb 15 16:47:11 hal kernel: [   19.753708] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3  
 Feb 15 16:47:11 hal kernel: [   19.753732] uhci_hcd 0000:00:1a.0: irq 19, io base 0x0000d880  
 Feb 15 16:47:11 hal kernel: [   19.753819] usb usb3: configuration #1 chosen from 1 choice  
 Feb 15 16:47:11 hal kernel: [   19.753834] hub 3-0:1.0: USB hub found  
 Feb 15 16:47:11 hal kernel: [   19.753838] hub 3-0:1.0: 2 ports detected  
 Feb 15 16:47:11 hal kernel: [   19.855592] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 20  
 Feb 15 16:47:11 hal kernel: [   19.855601] PCI: Setting latency timer of device 0000:00:1a.1 to 64  
 Feb 15 16:47:11 hal kernel: [   19.855604] uhci_hcd 0000:00:1a.1: UHCI Host Controller  
 Feb 15 16:47:11 hal kernel: [   19.855621] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4  
 Feb 15 16:47:11 hal kernel: [   19.855644] uhci_hcd 0000:00:1a.1: irq 20, io base 0x0000d800  
 Feb 15 16:47:11 hal kernel: [   19.855722] usb usb4: configuration #1 chosen from 1 choice  
 Feb 15 16:47:11 hal kernel: [   19.855737] hub 4-0:1.0: USB hub found  
 Feb 15 16:47:11 hal kernel: [   19.855741] hub 4-0:1.0: 2 ports detected  
 Feb 15 16:47:11 hal kernel: [   19.878725] ACPI: PCI Interrupt 0000:00:1a.2[D] -> GSI 17 (level, low) -> IRQ 16  
 Feb 15 16:47:11 hal kernel: [   19.878730] PCI: Setting latency timer of device 0000:00:1a.2 to 64  
 Feb 15 16:47:11 hal kernel: [   19.878733] uhci_hcd 0000:00:1a.2: UHCI Host Controller  
 Feb 15 16:47:11 hal kernel: [   19.878746] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5  
 Feb 15 16:47:11 hal kernel: [   19.878768] uhci_hcd 0000:00:1a.2: irq 16, io base 0x0000d480  
 Feb 15 16:47:11 hal kernel: [   19.878838] usb usb5: configuration #1 chosen from 1 choice  
 Feb 15 16:47:11 hal kernel: [   19.878852] hub 5-0:1.0: USB hub found  
 Feb 15 16:47:11 hal kernel: [   19.878855] hub 5-0:1.0: 2 ports detected  
 Feb 15 16:47:11 hal kernel: [   19.908343] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18  
 Feb 15 16:47:11 hal kernel: [   19.908348] PCI: Setting latency timer of device 0000:00:1d.0 to 64  
 Feb 15 16:47:11 hal kernel: [   19.908350] uhci_hcd 0000:00:1d.0: UHCI Host Controller  
 Feb 15 16:47:11 hal kernel: [   19.908363] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6  
 Feb 15 16:47:11 hal kernel: [   19.908382] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000d400  
 Feb 15 16:47:11 hal kernel: [   19.908452] usb usb6: configuration #1 chosen from 1 choice  
 Feb 15 16:47:11 hal kernel: [   19.908466] hub 6-0:1.0: USB hub found  
 Feb 15 16:47:11 hal kernel: [   19.908469] hub 6-0:1.0: 2 ports detected  
 Feb 15 16:47:11 hal kernel: [   19.938036] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 18 (level, low) -> IRQ 17  
 Feb 15 16:47:11 hal kernel: [   19.938042] PCI: Setting latency timer of device 0000:00:1d.1 to 64  
 Feb 15 16:47:11 hal kernel: [   19.938044] uhci_hcd 0000:00:1d.1: UHCI Host Controller  
 Feb 15 16:47:11 hal kernel: [   19.938064] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7  
 Feb 15 16:47:11 hal kernel: [   19.938082] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d080  
 Feb 15 16:47:11 hal kernel: [   19.938154] usb usb7: configuration #1 chosen from 1 choice  
 Feb 15 16:47:11 hal kernel: [   19.938168] hub 7-0:1.0: USB hub found  
 Feb 15 16:47:11 hal kernel: [   19.938171] hub 7-0:1.0: 2 ports detected  
 Feb 15 16:47:11 hal kernel: [   19.963073] Clocksource tsc unstable (delta = -319864781 ns)  
 Feb 15 16:47:11 hal kernel: [   19.968353] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 17  
 Feb 15 16:47:11 hal kernel: [   19.968357] PCI: Setting latency timer of device 0000:00:1d.2 to 64  
 Feb 15 16:47:11 hal kernel: [   19.968360] uhci_hcd 0000:00:1d.2: UHCI Host Controller  
 Feb 15 16:47:11 hal kernel: [   19.968374] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8  
 Feb 15 16:47:11 hal kernel: [   19.968392] uhci_hcd 0000:00:1d.2: irq 17, io base 0x0000d000  
 Feb 15 16:47:11 hal kernel: [   19.968460] usb usb8: configuration #1 chosen from 1 choice  
 Feb 15 16:47:11 hal kernel: [   19.968474] hub 8-0:1.0: USB hub found  
 Feb 15 16:47:11 hal kernel: [   19.968477] hub 8-0:1.0: 2 ports detected  
 Feb 15 16:47:11 hal kernel: [   19.977216] usb 3-1: new low speed USB device using uhci_hcd and address 2  
 Feb 15 16:47:11 hal kernel: [   19.999698] ahci 0000:00:1f.2: version 3.0  
 Feb 15 16:47:11 hal kernel: [   19.999720] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21  
 Feb 15 16:47:11 hal kernel: [   20.052761] usb 3-1: configuration #1 chosen from 1 choice  
 Feb 15 16:47:11 hal kernel: [   20.152317] usb 3-2: new low speed USB device using uhci_hcd and address 3  
 Feb 15 16:47:11 hal kernel: [   20.218060] usb 3-2: configuration #1 chosen from 1 choice  
 Feb 15 16:47:11 hal kernel: [   20.233595] usbcore: registered new interface driver hiddev  
 Feb 15 16:47:11 hal kernel: [   20.238389] input: Dell Dell USB Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input1  
 Feb 15 16:47:11 hal kernel: [   20.248213] input,hidraw0: USB HID v1.11 Mouse [Dell Dell USB Optical Mouse] on usb-0000:00:1a.0-1  
 Feb 15 16:47:11 hal kernel: [   20.257911] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input2  
 Feb 15 16:47:11 hal kernel: [   20.262541] input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1a.0-2  
 Feb 15 16:47:11 hal kernel: [   20.262560] usbcore: registered new interface driver usbhid  
 Feb 15 16:47:11 hal kernel: [   20.262565] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver  
 Feb 15 16:47:11 hal kernel: [   20.310866] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode  
 Feb 15 16:47:11 hal kernel: [   20.310874] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part  
 Feb 15 16:47:11 hal kernel: [   20.310881] PCI: Setting latency timer of device 0000:00:1f.2 to 64  
 Feb 15 16:47:11 hal kernel: [   20.311177] scsi0 : ahci  
 Feb 15 16:47:11 hal kernel: [   20.311327] scsi1 : ahci  
 Feb 15 16:47:11 hal kernel: [   20.311443] scsi2 : ahci  
 Feb 15 16:47:11 hal kernel: [   20.311557] scsi3 : ahci  
 Feb 15 16:47:11 hal kernel: [   20.311665] scsi4 : ahci  
 Feb 15 16:47:11 hal kernel: [   20.311775] scsi5 : ahci  
 Feb 15 16:47:11 hal kernel: [   20.311853] ata1: SATA max UDMA/133 abar m2048@0xfeafb000 port 0xfeafb100 irq 220  
 Feb 15 16:47:11 hal kernel: [   20.311855] ata2: SATA max UDMA/133 abar m2048@0xfeafb000 port 0xfeafb180 irq 220  
 Feb 15 16:47:11 hal kernel: [   20.311858] ata3: SATA max UDMA/133 abar m2048@0xfeafb000 port 0xfeafb200 irq 220  
 Feb 15 16:47:11 hal kernel: [   20.311860] ata4: SATA max UDMA/133 abar m2048@0xfeafb000 port 0xfeafb280 irq 220  
 Feb 15 16:47:11 hal kernel: [   20.311862] ata5: SATA max UDMA/133 abar m2048@0xfeafb000 port 0xfeafb300 irq 220  
 Feb 15 16:47:11 hal kernel: [   20.311864] ata6: SATA max UDMA/133 abar m2048@0xfeafb000 port 0xfeafb380 irq 220  
 Feb 15 16:47:11 hal kernel: [   20.389868] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)  
 Feb 15 16:47:11 hal kernel: [   20.402770] ata1.00: ATA-8: WDC WD1600AAJS-75M0A0, 01.03E01, max UDMA/133  
 Feb 15 16:47:11 hal kernel: [   20.402774] ata1.00: 312500000 sectors, multi 0: LBA48 NCQ (depth 31/32)  
 Feb 15 16:47:11 hal kernel: [   20.403600] ata1.00: configured for UDMA/133  
 Feb 15 16:47:11 hal kernel: [   20.457693] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)  
 Feb 15 16:47:11 hal kernel: [   20.475102] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-H653F, D300, max UDMA/100  
 Feb 15 16:47:11 hal kernel: [   20.475105] ata2.00: applying bridge limits  
 Feb 15 16:47:11 hal kernel: [   20.492676] ata2.00: configured for UDMA/100  
 Feb 15 16:47:11 hal kernel: [   20.527793] ata3: SATA link down (SStatus 0 SControl 300)  
 Feb 15 16:47:11 hal kernel: [   20.563250] ata4: SATA link down (SStatus 0 SControl 300)  
 Feb 15 16:47:11 hal kernel: [   20.598821] ata5: SATA link down (SStatus 0 SControl 300)  
 Feb 15 16:47:11 hal kernel: [   20.634099] ata6: SATA link down (SStatus 0 SControl 300)  
 Feb 15 16:47:11 hal kernel: [   20.634228] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-7 01.0 PQ: 0 ANSI: 5  
 Feb 15 16:47:11 hal kernel: [   20.634758] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-H653F D300 PQ: 0 ANSI: 5  
 Feb 15 16:47:11 hal kernel: [   20.640254] Driver 'sd' needs updating - please use bus_type methods  
 Feb 15 16:47:11 hal kernel: [   20.642011] Driver 'sr' needs updating - please use bus_type methods  
 Feb 15 16:47:11 hal kernel: [   20.644771] sd 0:0:0:0: [sda] 312500000 512-byte hardware sectors (160000 MB)  
 Feb 15 16:47:11 hal kernel: [   20.644790] sd 0:0:0:0: [sda] Write Protect is off  
 Feb 15 16:47:11 hal kernel: [   20.644792] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00  
 Feb 15 16:47:11 hal kernel: [   20.644823] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA  
 Feb 15 16:47:11 hal kernel: [   20.644875] sd 0:0:0:0: [sda] 312500000 512-byte hardware sectors (160000 MB)  
 Feb 15 16:47:11 hal kernel: [   20.644891] sd 0:0:0:0: [sda] Write Protect is off  
 Feb 15 16:47:11 hal kernel: [   20.644893] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00  
 Feb 15 16:47:11 hal kernel: [   20.644922] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA  
 Feb 15 16:47:11 hal kernel: [   20.644924]  sda: sda1 sda2 < sda5 >  
 Feb 15 16:47:11 hal kernel: [   20.666383] sd 0:0:0:0: [sda] Attached SCSI disk  
 Feb 15 16:47:11 hal kernel: [   20.669905] sd 0:0:0:0: Attached scsi generic sg0 type 0  
 Feb 15 16:47:11 hal kernel: [   20.669918] sr 1:0:0:0: Attached scsi generic sg1 type 5  
 Feb 15 16:47:11 hal kernel: [   20.670812] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray  
 Feb 15 16:47:11 hal kernel: [   20.670815] Uniform CD-ROM driver Revision: 3.20  
 Feb 15 16:47:11 hal kernel: [   20.670844] sr 1:0:0:0: Attached scsi CD-ROM sr0  
 Feb 15 16:47:11 hal kernel: [   23.622033] padlock: VIA PadLock Hash Engine not detected.  
 Feb 15 16:47:11 hal kernel: [   24.395592] Attempting manual resume  
 Feb 15 16:47:11 hal kernel: [   24.395595] swsusp: Resume From Partition 254:2  
 Feb 15 16:47:11 hal kernel: [   24.395596] PM: Checking swsusp image.  
 Feb 15 16:47:11 hal kernel: [   24.395825] PM: Resume from disk failed.  
 Feb 15 16:47:11 hal kernel: [   24.456594] kjournald starting.  Commit interval 5 seconds  
 Feb 15 16:47:11 hal kernel: [   24.456608] EXT3-fs: mounted filesystem with ordered data mode.  
 Feb 15 16:47:11 hal kernel: [   28.964317] input: PC Speaker as /devices/platform/pcspkr/input/input3 
 Feb 15 16:47:11 hal kernel: [   28.996621] input: Power Button (FF) as /devices/virtual/input/input4  
 Feb 15 16:47:11 hal kernel: [   29.010645] pci_hotplug: PCI Hot Plug PCI Core version: 0.5  
 Feb 15 16:47:11 hal kernel: [   29.018592] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4  
 Feb 15 16:47:11 hal kernel: [   29.293766] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)  
 Feb 15 16:47:11 hal kernel: [   29.409388] r8169: eth0: link down  
 Feb 15 16:47:11 hal kernel: [   29.423537] ACPI: Power Button (FF) [PWRF]  
 Feb 15 16:47:11 hal kernel: [   29.423605] input: Power Button (CM) as /devices/virtual/input/input5  
 Feb 15 16:47:11 hal kernel: [   29.543337] ACPI: Power Button (CM) [PWRB]  
 Feb 15 16:47:11 hal kernel: [   29.684167] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22  
 Feb 15 16:47:11 hal kernel: [   29.684188] PCI: Setting latency timer of device 0000:00:1b.0 to 64  
 Feb 15 16:47:11 hal kernel: [   29.762301] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...  
 Feb 15 16:47:11 hal kernel: [   30.337618] NET: Registered protocol family 17  
 Feb 15 16:47:11 hal kernel: [   30.765491] loop: module loaded  
 Feb 15 16:47:11 hal kernel: [   30.805934] lp: driver loaded but no devices found  
 Feb 15 16:47:11 hal kernel: [   30.881967] Adding 6119416k swap on /dev/mapper/hal-swap_1.  Priority:-1 extents:1 across:6119416k  
 Feb 15 16:47:11 hal kernel: [   31.294357] EXT3 FS on dm-1, internal journal  
 Feb 15 16:47:11 hal kernel: [   31.773913] kjournald starting.  Commit interval 5 seconds  
 Feb 15 16:47:11 hal kernel: [   31.774063] EXT3 FS on sda1, internal journal  
 Feb 15 16:47:11 hal kernel: [   31.774069] EXT3-fs: mounted filesystem with ordered data mode.  
 Feb 15 16:47:11 hal kernel: [   32.308073] ip_tables: (C) 2000-2006 Netfilter Core Team  
 Feb 15 16:47:11 hal kernel: [   32.337551] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)  
 Feb 15 16:47:11 hal kernel: [   32.430348] NET: Registered protocol family 10  
 Feb 15 16:47:11 hal kernel: [   32.430520] lo: Disabled Privacy Extensions  
 Feb 15 16:47:11 hal kernel: [   32.430780] ADDRCONF(NETDEV_UP): eth0: link is not ready  
 Feb 15 16:47:11 hal kernel: [   32.442937] ip6_tables: (C) 2000-2006 Netfilter Core Team  
 Feb 15 16:47:11 hal kernel: [   33.175379] No dock devices found.  
 Feb 15 16:47:11 hal NetworkManager: <info>  starting...  
 Feb 15 16:47:14 hal dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14  
 Feb 15 16:47:15 hal named[5245]: starting BIND 9.4.2-P2.1 -u bind  
 Feb 15 16:47:15 hal named[5245]: found 2 CPUs, using 2 worker threads  
 Feb 15 16:47:15 hal named[5245]: loading configuration from '/etc/bind/named.conf'  
 Feb 15 16:47:15 hal named[5245]: listening on IPv6 interfaces, port 53  
 Feb 15 16:47:15 hal kernel: [   36.318669] audit(1266270435.372:2): type=1503 operation="capable" name="sys_resource" pid=5246 profile="/usr/sbin/named" namespace="default"  
 Feb 15 16:47:15 hal named[5245]: listening on IPv4 interface lo, 127.0.0.1#53  
 Feb 15 16:47:15 hal named[5245]: automatic empty zone: 254.169.IN-ADDR.ARPA  
 Feb 15 16:47:15 hal named[5245]: automatic empty zone: 2.0.192.IN-ADDR.ARPA  
 Feb 15 16:47:15 hal named[5245]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA  
 Feb 15 16:47:15 hal named[5245]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA 
 Feb 15 16:47:15 hal named[5245]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA 
 Feb 15 16:47:15 hal named[5245]: automatic empty zone: D.F.IP6.ARPA  
 Feb 15 16:47:15 hal named[5245]: automatic empty zone: 8.E.F.IP6.ARPA  
 Feb 15 16:47:15 hal named[5245]: automatic empty zone: 9.E.F.IP6.ARPA  
 Feb 15 16:47:15 hal named[5245]: automatic empty zone: A.E.F.IP6.ARPA  
 Feb 15 16:47:15 hal named[5245]: automatic empty zone: B.E.F.IP6.ARPA  
 Feb 15 16:47:15 hal named[5245]: command channel listening on 127.0.0.1#953  
 Feb 15 16:47:15 hal named[5245]: command channel listening on ::1#953  
 Feb 15 16:47:15 hal named[5245]: zone 0.in-addr.arpa/IN: loaded serial 1  
 Feb 15 16:47:15 hal named[5245]: zone 192.168.0.in-addr.arpa/IN: loaded serial 1  
 Feb 15 16:47:15 hal named[5245]: zone 127.in-addr.arpa/IN: loaded serial 1  
 Feb 15 16:47:15 hal named[5245]: zone 255.in-addr.arpa/IN: loaded serial 1  
 Feb 15 16:47:15 hal named[5245]: zone localhost/IN: loaded serial 2  
 Feb 15 16:47:15 hal named[5245]: zone ifantasysports.net/IN: loaded serial 2  
 Feb 15 16:47:15 hal named[5245]: running  
 Feb 15 16:47:16 hal avahi-daemon[5301]: Found user 'avahi' (UID 113) and group 'avahi' (GID 127).  
 Feb 15 16:47:16 hal avahi-daemon[5301]: Successfully dropped root privileges.  
 Feb 15 16:47:16 hal avahi-daemon[5301]: avahi-daemon 0.6.22 starting up.  
 Feb 15 16:47:16 hal avahi-daemon[5301]: Successfully called chroot().  
 Feb 15 16:47:16 hal avahi-daemon[5301]: Successfully dropped remaining capabilities.  
 Feb 15 16:47:16 hal avahi-daemon[5301]: No service file found in /etc/avahi/services.  
 Feb 15 16:47:16 hal avahi-daemon[5301]: Network interface enumeration completed.  
 Feb 15 16:47:16 hal avahi-daemon[5301]: Registering HINFO record with values 'I686'/'LINUX'.  
 Feb 15 16:47:16 hal avahi-daemon[5301]: Server startup complete. Host name is hal.local. Local service cookie is 3432749354.  
 Feb 15 16:47:17 hal mysqld_safe[5393]: started  
 Feb 15 16:47:18 hal mysqld[5396]: 100215 16:47:18  InnoDB: Started; log sequence number 0 43655  
 Feb 15 16:47:18 hal mysqld[5396]: 100215 16:47:18 [Note] /usr/sbin/mysqld: ready for connections.  
 Feb 15 16:47:18 hal mysqld[5396]: Version: '5.0.51a-3ubuntu5.5'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)  
 Feb 15 16:47:19 hal /etc/mysql/debian-start[5434]: Upgrading MySQL tables if necessary.  
 Feb 15 16:47:19 hal /etc/mysql/debian-start[5440]: Looking for 'mysql' in: /usr/bin/mysql 
 Feb 15 16:47:19 hal /etc/mysql/debian-start[5440]: Looking for 'mysqlcheck' in: /usr/bin/mysqlcheck  
 Feb 15 16:47:19 hal /etc/mysql/debian-start[5440]: This installation of MySQL is already upgraded to 5.0.51a, use --force if you still need to run mysql_upgrade  
 Feb 15 16:47:19 hal /etc/mysql/debian-start[5454]: Checking for insecure root accounts.  
 Feb 15 16:47:19 hal /etc/mysql/debian-start[5458]: Checking for crashed MySQL tables.  
 Feb 15 16:47:19 hal kernel: [   38.353611] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)  
 Feb 15 16:47:19 hal kernel: [   38.353615] apm: disabled - APM is not SMP safe.  
 Feb 15 16:47:21 hal postfix/master[5548]: daemon started -- version 2.5.1, configuration /etc/postfix  
 Feb 15 16:47:22 hal ntpd[5640]: ntpd 4.2.4p4@1.1520-o Fri Dec  4 18:18:33 UTC 2009 (1)  
 Feb 15 16:47:22 hal ntpd[5642]: precision = 1.000 usec  
 Feb 15 16:47:22 hal ntpd[5642]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled  
 Feb 15 16:47:22 hal ntpd[5642]: Listening on interface #1 wildcard, ::#123 Disabled  
 Feb 15 16:47:22 hal ntpd[5642]: Listening on interface #2 lo, ::1#123 Enabled  
 Feb 15 16:47:22 hal ntpd[5642]: Listening on interface #3 lo, 127.0.0.1#123 Enabled  
 Feb 15 16:47:22 hal ntpd[5642]: kernel time sync status 0040  
 Feb 15 16:47:22 hal dhcdbd: Started up. 
 Feb 15 16:47:23 hal ntpd[5642]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift  
 Feb 15 16:47:23 hal dovecot: Dovecot v1.0.10 starting up  
 Feb 15 16:47:24 hal NetworkManager: <debug> [1266270444.510940] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD__RW_TS_H653F').  
 Feb 15 16:47:25 hal ntpd_initres[5664]: host name not found: ntp.ubuntu.com  
 Feb 15 16:47:25 hal ntpd_initres[5664]: couldn't resolve `ntp.ubuntu.com', giving up on it  
 Feb 15 16:47:25 hal ntpd_initres[5664]: host name not found: time.nrc.ca  
 Feb 15 16:47:25 hal ntpd_initres[5664]: couldn't resolve `time.nrc.ca', giving up on it  
 Feb 15 16:47:26 hal kernel: [   43.105648] mtrr: no more MTRRs available  
 Feb 15 16:47:26 hal kernel: [   43.105693] mtrr: no more MTRRs available  
 Feb 15 16:47:26 hal kernel: [   43.105721] mtrr: no more MTRRs available  
 Feb 15 16:47:26 hal kernel: [   43.105748] mtrr: no more MTRRs available  
 Feb 15 16:47:27 hal squid[5874]: Squid Parent: child process 5877 started  
 Feb 15 16:47:27 hal squid[5877]: Starting Squid Cache version 2.6.STABLE18 for i386-debian-linux-gnu...  
 Feb 15 16:47:27 hal squid[5877]: Process ID 5877  
 Feb 15 16:47:27 hal squid[5877]: With 1024 file descriptors available  
 Feb 15 16:47:27 hal squid[5877]: Using epoll for the IO loop  
 Feb 15 16:47:27 hal squid[5877]: DNS Socket created at 0.0.0.0, port 56952, FD 6  
 Feb 15 16:47:27 hal squid[5877]: Adding domain cgocable.net from /etc/resolv.conf  
 Feb 15 16:47:27 hal squid[5877]: Adding nameserver 192.168.1.1 from /etc/resolv.conf  
 Feb 15 16:47:27 hal squid[5877]: Adding nameserver 24.226.1.93 from /etc/resolv.conf  
 Feb 15 16:47:27 hal squid[5877]: Adding nameserver 24.226.10.193 from /etc/resolv.conf  
 Feb 15 16:47:27 hal squid[5877]: User-Agent logging is disabled.  
 Feb 15 16:47:27 hal squid[5877]: Referer logging is disabled.  
 Feb 15 16:47:27 hal anacron[5898]: Anacron 2.3 started on 2010-02-15  
 Feb 15 16:47:27 hal anacron[5898]: Will run job `cron.weekly' in 10 min.  
 Feb 15 16:47:27 hal anacron[5898]: Jobs will be executed sequentially  
 Feb 15 16:47:27 hal /usr/sbin/cron[5926]: (CRON) INFO (pidfile fd = 3)  
 Feb 15 16:47:27 hal /usr/sbin/cron[5927]: (CRON) STARTUP (fork ok)  
 Feb 15 16:47:27 hal squid[5877]: Unlinkd pipe opened on FD 11  
 Feb 15 16:47:27 hal squid[5877]: Swap maxSize 102400 KB, estimated 7876 objects  
 Feb 15 16:47:27 hal squid[5877]: Target number of buckets: 393  
 Feb 15 16:47:27 hal squid[5877]: Using 8192 Store buckets  
 Feb 15 16:47:27 hal squid[5877]: Max Mem  size: 8192 KB  
 Feb 15 16:47:27 hal /usr/sbin/cron[5927]: (CRON) INFO (Running @reboot jobs)  
 Feb 15 16:47:27 hal squid[5877]: Max Swap size: 102400 KB  
 Feb 15 16:47:27 hal squid[5877]: Local cache digest enabled; rebuild/rewrite every 3600/3600 sec  
 Feb 15 16:47:27 hal squid[5877]: Rebuilding storage in /var/spool/squid (CLEAN)  
 Feb 15 16:47:27 hal squid[5877]: Using Least Load store dir selection  
 Feb 15 16:47:27 hal squid[5877]: Set Current Directory to /var/spool/squid  
 Feb 15 16:47:28 hal dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12  
 Feb 15 16:47:28 hal squid[5877]: Loaded Icons.  
 Feb 15 16:47:28 hal squid[5877]: Accepting proxy HTTP connections at 0.0.0.0, port 8888, FD 13.  
 Feb 15 16:47:28 hal squid[5877]: Accepting ICP messages at 0.0.0.0, port 3130, FD 14.  
 Feb 15 16:47:28 hal squid[5877]: HTCP Disabled.  
 Feb 15 16:47:28 hal squid[5877]: WCCP Disabled.  
 Feb 15 16:47:28 hal squid[5877]: Ready to serve requests.  
 Feb 15 16:47:28 hal squid[5877]: Done reading /var/spool/squid swaplog (0 entries)  
 Feb 15 16:47:28 hal squid[5877]: Finished rebuilding storage from disk.  
 Feb 15 16:47:28 hal squid[5877]:         0 Entries scanned  
 Feb 15 16:47:28 hal squid[5877]:         0 Invalid entries.  
 Feb 15 16:47:28 hal squid[5877]:         0 With invalid flags.  
 Feb 15 16:47:28 hal squid[5877]:         0 Objects loaded.  
 Feb 15 16:47:28 hal squid[5877]:         0 Objects expired.  
 Feb 15 16:47:28 hal squid[5877]:         0 Objects cancelled.  
 Feb 15 16:47:28 hal squid[5877]:         0 Duplicate URLs purged.  
 Feb 15 16:47:28 hal squid[5877]:         0 Swapfile clashes avoided.  
 Feb 15 16:47:28 hal squid[5877]:   Took 0.9 seconds (   0.0 objects/sec).  
 Feb 15 16:47:28 hal squid[5877]: Beginning Validation Procedure  
 Feb 15 16:47:28 hal squid[5877]:   Completed Validation Procedure  
 Feb 15 16:47:28 hal squid[5877]:   Validated 0 Entries  
 Feb 15 16:47:28 hal squid[5877]:   store_swap_size = 0k  
 Feb 15 16:47:28 hal squid[5877]: storeLateRelease: released 0 objects  
 Feb 15 16:47:31 hal tomcat5.5: -e The java-gcj-compat-dev environment currently doesn't  
 Feb 15 16:47:31 hal tomcat5.5: support a security manager. See README.Debian.  
 Feb 15 16:47:39 hal dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19  
 Feb 15 16:47:46 hal jsvc.exec[5991]: Created MBeanServer with ID: 8htnd:g5psqouj.0:hal:1  
 Feb 15 16:47:49 hal jsvc.exec[5991]: 15-Feb-10 4:47:48 PM org.apache.catalina.core.AprLifecycleListener lifecycleEvent INFO: The Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: /usr/lib/../lib/gcj-4.2-81:/usr/lib/jni  
 Feb 15 16:47:49 hal jsvc.exec[5991]: 15-Feb-10 4:47:49 PM org.apache.coyote.http11.Http11BaseProtocol init INFO: Initializing Coyote HTTP/1.1 on http-8180  
 Feb 15 16:47:49 hal jsvc.exec[5991]: 15-Feb-10 4:47:49 PM org.apache.catalina.startup.Catalina load INFO: Initialization processed in 1984 ms  
 Feb 15 16:47:49 hal jsvc.exec[5991]: 15-Feb-10 4:47:49 PM org.apache.catalina.core.StandardService start INFO: Starting service Catalina  
 Feb 15 16:47:49 hal jsvc.exec[5991]: 15-Feb-10 4:47:49 PM org.apache.catalina.core.StandardEngine start INFO: Starting Servlet Engine: Apache Tomcat/5.5  
 Feb 15 16:47:49 hal jsvc.exec[5991]: 15-Feb-10 4:47:49 PM org.apache.catalina.core.StandardHost start INFO: XML validation disabled  
 Feb 15 16:47:54 hal jsvc.exec[5991]: 15-Feb-10 4:47:54 PM org.apache.catalina.core.ApplicationContext log INFO: ContextListener: contextInitialized()  
 Feb 15 16:47:54 hal jsvc.exec[5991]: 15-Feb-10 4:47:54 PM org.apache.catalina.core.ApplicationContext log INFO: SessionListener: contextInitialized()  
 Feb 15 16:47:56 hal jsvc.exec[5991]: 15-Feb-10 4:47:56 PM org.apache.catalina.core.ApplicationContext log INFO: ContextListener: attributeAdded('org.apache.catalina.Registry', 'org.apache.commons.modeler.Registry@73b220')  
 Feb 15 16:47:56 hal jsvc.exec[5991]: 15-Feb-10 4:47:56 PM org.apache.catalina.core.ApplicationContext log INFO: ContextListener: attributeAdded('org.apache.catalina.MBeanServer', 'mx4j.server.MX4JMBeanServer@46ab40')  
 Feb 15 16:47:59 hal dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8  
 Feb 15 16:47:59 hal NetworkManager: <info>  Updating allowed wireless network lists.  
 Feb 15 16:47:59 hal NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..  
 Feb 15 16:48:01 hal jsvc.exec[5991]: 15-Feb-10 4:48:01 PM org.apache.catalina.core.ApplicationContext log INFO: ContextListener: contextInitialized()  
 Feb 15 16:48:01 hal jsvc.exec[5991]: 15-Feb-10 4:48:01 PM org.apache.catalina.core.ApplicationContext log INFO: SessionListener: contextInitialized()  
 Feb 15 16:48:02 hal jsvc.exec[5991]: 15-Feb-10 4:48:02 PM org.apache.catalina.core.ApplicationContext log INFO: ContextListener: attributeAdded('org.apache.catalina.Registry', 'org.apache.commons.modeler.Registry@73b220')  
 Feb 15 16:48:02 hal jsvc.exec[5991]: 15-Feb-10 4:48:02 PM org.apache.catalina.core.ApplicationContext log INFO: ContextListener: attributeAdded('org.apache.catalina.MBeanServer', 'mx4j.server.MX4JMBeanServer@46ab40')  
 Feb 15 16:48:02 hal jsvc.exec[5991]: 15-Feb-10 4:48:02 PM org.apache.catalina.core.ApplicationContext log INFO: org.apache.webapp.balancer.BalancerFilter: init(): ruleChain: [org.apache.webapp.balancer.RuleChain: [org.apache.webapp.balancer.rules.URLStringMatchRule: Target string: News / Redirect URL: http://www.cnn.com], [org.apache.webapp.balancer.rules.RequestParameterRule: Target param name: paramName / Target param value: paramValue / Redirect URL: http://www.yahoo.com], [org.apache.webapp.balancer.rules.AcceptEverythingRule: Redirect URL: http://jakarta.apache.org]]  
 Feb 15 16:48:03 hal jsvc.exec[5991]: 15-Feb-10 4:48:03 PM org.apache.coyote.http11.Http11BaseProtocol start INFO: Starting Coyote HTTP/1.1 on http-8180  
 Feb 15 16:48:03 hal jsvc.exec[5991]: 15-Feb-10 4:48:03 PM org.apache.commons.modeler.modules.MbeansDescriptorsDOMSource execute SEVERE: Error reading descriptors  gnu.xml.dom.ls.DomLSException    at gnu.xml.dom.ls.DomLSParser.doParse(libgcj.so.81)    at gnu.xml.dom.ls.DomLSParser.parse(libgcj.so.81)    at gnu.xml.dom.DomDocumentBuilder.parse(libgcj.so.81)    at org.apache.commons.modeler.util.DomUtil.readXml(DomUtil.java:257)    at org.apache.commons.modeler.modules.MbeansDescriptorsDOMSource.execute(MbeansDescriptorsDOMSource.java:88)    at org.apache.commons.modeler.modules.MbeansDescriptorsDOMSource.loadDescriptors(MbeansDescriptorsDOMSource.java:78)    at org.apache.commons.modeler.Registry.load(Registry.java:792)    at org.apache.commons.modeler.Registry.loadDescriptors(Registry.java:901)    at org.apache.commons.modeler  
 Feb 15 16:48:03 hal jsvc.exec[5991]: .Registry.loadDescriptors(Registry.java:882)    at org.apache.commons.modeler.Registry.findDescriptor(Registry.java:961)    at org.apache.commons.modeler.Registry.findManagedBean(Registry.java:666)    at org.apache.commons.modeler.Registry.findManagedBean(Registry.java:1015)    at org.apache.commons.modeler.Registry.registerComponent(Registry.java:832)    at org.apache.catalina.connector.Connector.start(Connector.java:1077)    at org.apache.catalina.core.StandardService.start(StandardService.java:457)    at org.apache.catalina.core.StandardServer.start(StandardServer.java:700)    at org.apache.catalina.startup.Catalina.start(Catalina.java:552)    at java.lang.reflect.Method.invoke(libgcj.so.81)    at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:295)    at java.lang.reflect.Method.invoke(libgcj.so.81)    at org.apache.commons.daemon.support.DaemonLoader.start(DaemonLoader.java:177) Caused by: org.xml.sax.SAXParseException    at gnu.xml.stream.SAXParser.parse  
 Feb 15 16:48:03 hal jsvc.exec[5991]: mLSParser.doParse(libgcj.so.81)    ...20 more Caused by: javax.xml.stream.XMLStreamException    at gnu.xml.stream.XMLParser.next(libgcj.so.81)    at gnu.xml.stream.XMLParser.hasNext(libgcj.so.81)    at gnu.xml.stream.SAXParser.parse(libgcj.so.81)    ...21 more Caused by: java.io.IOException: error resolving http://jakarta.apache.org/commons/dtds/mbeans-descriptors.dtd    at gnu.xml.stream.XMLParser.resolve(libgcj.so.81)    at gnu.xml.stream.XMLParser.pushInput(libgcj.so.81)    at gnu.xml.stream.XMLParser.readDoctypeDecl(libgcj.so.81)    at gnu.xml.stream.XMLParser.next(libgcj.so.81)    ...23 more Caused by: java.net.UnknownHostException: jakarta.apache.org:80    at gnu.java.net.PlainSocketImpl.connect(libgcj.so.81)    at java.net.Socket.connect(libgcj.so.81)    at java.net.Socket.connect(libgcj.so.81)    at gnu.java.net.protocol.http.HTTPConnection.getSocket(libgcj.so.81)    at gnu.java.net.protocol.http.HTTPConnection.getOutputStream(libgcj.so.81)    at gnu.java  
 Feb 15 16:48:03 hal jsvc.exec[5991]: .net.protocol.http.Request.dispatch(libgcj.so.81)    at gnu.java.net.protocol.http.HTTPURLConnection.connect(libgcj.so.81)    at gnu.java.net.protocol.http.HTTPURLConnection.getInputStream(libgcj.so.81)    at java.net.URL.openStream(libgcj.so.81)    at gnu.xml.stream.XMLParser.resolve(libgcj.so.81)    ...26 more  
 Feb 15 16:48:04 hal jsvc.exec[5991]: 15-Feb-10 4:48:04 PM org.apache.jk.common.ChannelSocket init INFO: JK: ajp13 listening on /0.0.0.0:8009  
 Feb 15 16:48:04 hal jsvc.exec[5991]: 15-Feb-10 4:48:04 PM org.apache.jk.server.JkMain start INFO: Jk running ID=0 time=0/260  config=null  
 Feb 15 16:48:04 hal jsvc.exec[5991]: 15-Feb-10 4:48:04 PM org.apache.catalina.storeconfig.StoreLoader load INFO: Find registry server-registry.xml at classpath resource  
 Feb 15 16:48:04 hal jsvc.exec[5991]: 15-Feb-10 4:48:04 PM org.apache.catalina.startup.Catalina start INFO: Server startup in 15177 ms  
 Feb 15 16:48:07 hal dhclient: No DHCPOFFERS received.  
 Feb 15 16:48:07 hal dhclient: No working leases in persistent database - sleeping.  
 Feb 15 16:48:07 hal avahi-autoipd(eth0)[6410]: Found user 'avahi-autoipd' (UID 109) and group 'avahi-autoipd' (GID 121).  
 Feb 15 16:48:07 hal avahi-autoipd(eth0)[6410]: Successfully called chroot().  
 Feb 15 16:48:07 hal avahi-autoipd(eth0)[6410]: Successfully dropped root privileges.  
 Feb 15 16:48:07 hal avahi-autoipd(eth0)[6410]: Starting with address 169.254.7.74  
 Feb 15 16:48:13 hal avahi-autoipd(eth0)[6410]: Callout BIND, address 169.254.7.74 on interface eth0  
 Feb 15 16:48:13 hal avahi-daemon[5301]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.7.74.  
 Feb 15 16:48:13 hal avahi-daemon[5301]: New relevant interface eth0.IPv4 for mDNS.  
 Feb 15 16:48:13 hal avahi-daemon[5301]: Registering new address record for 169.254.7.74 on eth0.IPv4.  
 Feb 15 16:48:17 hal avahi-autoipd(eth0)[6410]: Successfully claimed IP address 169.254.7.74  
 Feb 15 16:48:17 hal ntpd[5642]: ntpd exiting on signal 15  
 Feb 15 16:48:17 hal postfix/master[5548]: reload configuration /etc/postfix  
 Feb 15 16:49:13 hal ntpdate[6492]: can't find host ntp.ubuntu.com  
 Feb 15 16:50:09 hal ntpdate[6492]: can't find host time.nrc.ca  
 Feb 15 16:50:09 hal ntpdate[6492]: no servers can be used, exiting  
 Feb 15 16:50:09 hal ntpd[6547]: ntpd 4.2.4p4@1.1520-o Fri Dec  4 18:18:33 UTC 2009 (1)  
 Feb 15 16:50:09 hal ntpd[6548]: precision = 1.000 usec  
 Feb 15 16:50:09 hal ntpd[6548]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled  
 Feb 15 16:50:09 hal ntpd[6548]: Listening on interface #1 wildcard, ::#123 Disabled  
 Feb 15 16:50:09 hal ntpd[6548]: Listening on interface #2 lo, ::1#123 Enabled  
 Feb 15 16:50:09 hal ntpd[6548]: Listening on interface #3 lo, 127.0.0.1#123 Enabled  
 Feb 15 16:50:09 hal ntpd[6548]: Listening on interface #4 eth0:avahi, 169.254.7.74#123 Enabled  
 Feb 15 16:50:09 hal ntpd[6548]: kernel time sync status 0040  
 Feb 15 16:50:09 hal ntpd[6548]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift  
 Feb 15 16:52:59 hal ntpd_initres[6549]: host name not found: ntp.ubuntu.com  
 Feb 15 16:52:59 hal ntpd_initres[6549]: couldn't resolve `ntp.ubuntu.com', giving up on it  
 Feb 15 16:53:55 hal ntpd_initres[6549]: host name not found: time.nrc.ca  
 Feb 15 16:53:55 hal ntpd_initres[6549]: couldn't resolve `time.nrc.ca', giving up on it  
 Feb 15 16:54:45 hal dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5  
 Feb 15 16:54:50 hal dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14  
 Feb 15 16:55:04 hal dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9  
 Feb 15 16:55:13 hal dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18  
 Feb 15 16:55:31 hal dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15  
 Feb 15 16:55:46 hal dhclient: No DHCPOFFERS received.  
 Feb 15 16:55:46 hal dhclient: No working leases in persistent database - sleeping.  
 Feb 15 16:57:27 hal anacron[5898]: Job `cron.weekly' started  
 Feb 15 16:57:27 hal anacron[6559]: Updated timestamp for job `cron.weekly' to 2010-02-15  
 Feb 15 16:57:35 hal syslogd 1.5.0#1ubuntu1: restart.  
 Feb 15 16:57:35 hal anacron[5898]: Job `cron.weekly' terminated  
 Feb 15 16:57:35 hal anacron[5898]: Normal exit (1 job run)  
 Feb 15 17:02:21 hal dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6  
 Feb 15 17:02:27 hal dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11  
 Feb 15 17:02:38 hal dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9  
 Feb 15 17:02:47 hal dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20  
 Feb 15 17:03:07 hal dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8  
 Feb 15 17:03:15 hal dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7  
 Feb 15 17:03:22 hal dhclient: No DHCPOFFERS received.  
 Feb 15 17:03:22 hal dhclient: No working leases in persistent database - sleeping.  
 

```I still have my machine on and it's still running the same process that you see above. I also tried to access my log files from before 13-Feb, but they are no longer visible?
 
Does anyone know what the cause/solution of this problem could be?

---

