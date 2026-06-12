---
title: "Maverick freeze, no answer"
date: 2011-02-02
forum: General Help
---

### Post by runeh76 on 2011-02-02
Hi guys :)

I was surfing internet yesterday evening with chromium and suddenly whole ubuntu did hang up. Didnt answer to any key or mouse, just last net-site was open and keyboard was blinking CapsLock&ScrollLock. Before it and now net-sites opens little slower, than usually.  Couldnt do nothing else, just shutdown from front panel button.

How can i find out, what did cause this? Maybe some log?


....tryed to post this yesterday, but it took 2minutes and error "(net::ERR_NAME_NOT_RESOLVED)" 

(Internet connection is 3G)

---

### Post by [Snc] on 2011-02-02
Hey there!

> ....tryed to post this yesterday, but it took 2minutes and error "(net::ERR_NAME_NOT_RESOLVED)" 
The forum is slightly slow, canonical is trying its best, read more about this here:
```
http://ubuntuforums.org/announcement.php?f=331
```

Whenever my num, caps and scroll lock lights blink, i know, that my comp has crashed (kernel panic), in my case it is my motherboards fault in other cases it can be overheating, wrong drivers, bad disk, .... in short, something went wrong really bad (i guess i didn't tell you anything new here :))

well, the logs are here

```

**/var/log/messages** : General log messages
 **/var/log/boot** : System boot log
 **/var/log/debug** : Debugging log messages
 **/var/log/auth.log** : User login and authentication logs
 **/var/log/daemon.log** : Running services such as squid, ntpd and others log message to this file
 **/var/log/dmesg** : Linux kernel  ring buffer log
 **/var/log/dpkg.log** : All binary package log includes package installation and other information
 **/var/log/faillog** : User failed login log file
 **/var/log/kern.log** : Kernel log file
 **/var/log/lpr.log** : Printer log file
 **/var/log/mail.*** : All mail server message log files
 **/var/log/mysql.*** : MySQL server log file
 **/var/log/user.log** : All userlevel logs
 **/var/log/xorg.0.log** : X.org log file
 **/var/log/apache2/*** : Apache web server log files directory
 **/var/log/lighttpd/*** : Lighttpd web server log files directory
 **/var/log/fsck/*** : fsck command log
 **/var/log/apport.log** : Application crash report / log file

```

And a GUI viewer can be run from terminal like this:
```
gnome-system-log
```

---

### Post by [Snc] on 2011-02-02
PS. ERR_NAME_NOT_RESOLVED = DNS problems, so your connection was sluggish ... 3G can do that sometimes ...

---

### Post by runeh76 on 2011-02-02
:)  Thank you Snc!!

I was thinking same, that heat is the problem (my computer is on around 10h and im playing lots Flash-games, one game heating graphic-gard). Im gonna buy extra-fan to ventilation and see if it gonna help little.

Okay i was reading var/log/sys.log. Im still learning this u know, so could u say what log i should check? I can also paste it here. Im going to buy that fan now, so im back here a little bit later..

Thx again!

---

### Post by runeh76 on 2011-02-02
Here is **gnome-system-log**


```
Feb  1 21:06:13 Masiina moblock: OUT: Level 3 Communications,hits: 1,DST: 4.2.2.1
Feb  1 21:06:14 Masiina moblock: OUT: Level 3 Communications,hits: 2,DST: 4.2.2.2
Feb  1 21:06:15 Masiina kernel: [   64.590197] lo: Disabled Privacy Extensions
Feb  1 21:06:19 Masiina moblock: OUT: Level 3 Communications,hits: 3,DST: 4.2.2.1
Feb  1 21:06:20 Masiina moblock: OUT: Level 3 Communications,hits: 4,DST: 4.2.2.2
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 5,DST: 4.2.2.1
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 6,DST: 4.2.2.2
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 7,DST: 4.2.2.1
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 8,DST: 4.2.2.2
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 9,DST: 4.2.2.1
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 10,DST: 4.2.2.1
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 11,DST: 4.2.2.2
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 12,DST: 4.2.2.2
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 13,DST: 4.2.2.1
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 14,DST: 4.2.2.2
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 15,DST: 4.2.2.1
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 16,DST: 4.2.2.2
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 17,DST: 4.2.2.1
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 18,DST: 4.2.2.2
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 19,DST: 4.2.2.1
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 20,DST: 4.2.2.2
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 21,DST: 4.2.2.1
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 22,DST: 4.2.2.2
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 23,DST: 4.2.2.1
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 24,DST: 4.2.2.2
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 25,DST: 4.2.2.1
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 26,DST: 4.2.2.2
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 27,DST: 4.2.2.1
Feb  1 21:06:22 Masiina moblock: OUT: Level 3 Communications,hits: 28,DST: 4.2.2.2
Feb  1 21:06:23 Masiina moblock: OUT: Level 3 Communications,hits: 29,DST: 4.2.2.1
Feb  1 21:06:23 Masiina moblock: OUT: Level 3 Communications,hits: 30,DST: 4.2.2.2
Feb  1 21:06:23 Masiina moblock: OUT: Level 3 Communications,hits: 31,DST: 4.2.2.1
Feb  1 21:06:23 Masiina moblock: OUT: Level 3 Communications,hits: 32,DST: 4.2.2.2
Feb  1 21:06:23 Masiina moblock: OUT: Level 3 Communications,hits: 33,DST: 4.2.2.1
Feb  1 21:06:23 Masiina moblock: OUT: Level 3 Communications,hits: 34,DST: 4.2.2.1
Feb  1 21:06:23 Masiina moblock: OUT: Level 3 Communications,hits: 35,DST: 4.2.2.2
Feb  1 21:06:23 Masiina moblock: OUT: Level 3 Communications,hits: 36,DST: 4.2.2.2
Feb  1 21:06:23 Masiina moblock: OUT: Level 3 Communications,hits: 37,DST: 4.2.2.1
Feb  1 21:06:23 Masiina moblock: OUT: Level 3 Communications,hits: 38,DST: 4.2.2.1
Feb  1 21:06:23 Masiina moblock: OUT: Level 3 Communications,hits: 39,DST: 4.2.2.2
Feb  1 21:06:23 Masiina moblock: OUT: Level 3 Communications,hits: 40,DST: 4.2.2.2
Feb  1 21:06:33 Masiina kernel: [   82.853679] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
Feb  1 21:06:34 Masiina kernel: [   83.644026] Clocksource tsc unstable (delta = -95081250 ns)
Feb  1 21:11:06 Masiina moblock: OUT: SoftLayer Technologies,hits: 1,DST: 74.86.45.187
Feb  1 21:11:06 Masiina moblock: OUT: SoftLayer Technologies,hits: 1,DST: 75.126.175.248
Feb  1 21:11:16 Masiina moblock: OUT: Peer 1 Network,hits: 1,DST: 64.34.170.30
Feb  1 21:22:19 Masiina kernel: [ 1028.344235] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=68.84.148.164 DST=85.77.159.2 LEN=52 TOS=0x00 PREC=0x00 TTL=113 ID=53050 DF PROTO=TCP SPT=38018 DPT=48209 WINDOW=8192 RES=0x00 SYN URGP=0 MARK=0x14 
Feb  1 21:22:22 Masiina kernel: [ 1031.353576] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=68.84.148.164 DST=85.77.159.2 LEN=52 TOS=0x00 PREC=0x00 TTL=113 ID=49936 DF PROTO=TCP SPT=38018 DPT=48209 WINDOW=8192 RES=0x00 SYN URGP=0 MARK=0x14 
Feb  1 21:22:28 Masiina kernel: [ 1037.392208] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=68.84.148.164 DST=85.77.159.2 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=36964 DF PROTO=TCP SPT=38018 DPT=48209 WINDOW=8192 RES=0x00 SYN URGP=0 MARK=0x14 
Feb  1 22:19:34 Masiina kernel: imklog 4.2.0, log source = /proc/kmsg started.
```


Here is **sys.log**

```
Feb  1 21:06:29 Masiina ntpd[2372]: frequency initialized -70.702 PPM from /var/lib/ntp/ntp.drift
Feb  1 21:06:33 Masiina kernel: [   82.853679] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
Feb  1 21:06:34 Masiina kernel: [   83.644026] Clocksource tsc unstable (delta = -95081250 ns)
Feb  1 21:11:06 Masiina moblock: OUT: SoftLayer Technologies,hits: 1,DST: 74.86.45.187
Feb  1 21:11:06 Masiina moblock: OUT: SoftLayer Technologies,hits: 1,DST: 75.126.175.248
Feb  1 21:11:16 Masiina moblock: OUT: Peer 1 Network,hits: 1,DST: 64.34.170.30
Feb  1 21:12:53 Masiina ntpd[2372]: synchronized to 91.189.94.4, stratum 2
Feb  1 21:12:53 Masiina ntpd[2372]: kernel time sync status change 2001
Feb  1 21:17:01 Masiina CRON[2718]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb  1 21:22:19 Masiina kernel: [ 1028.344235] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=68.84.148.164 DST=85.77.159.2 LEN=52 TOS=0x00 PREC=0x00 TTL=113 ID=53050 DF PROTO=TCP SPT=38018 DPT=48209 WINDOW=8192 RES=0x00 SYN URGP=0 MARK=0x14 
Feb  1 21:22:22 Masiina kernel: [ 1031.353576] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=68.84.148.164 DST=85.77.159.2 LEN=52 TOS=0x00 PREC=0x00 TTL=113 ID=49936 DF PROTO=TCP SPT=38018 DPT=48209 WINDOW=8192 RES=0x00 SYN URGP=0 MARK=0x14 
Feb  1 21:22:28 Masiina kernel: [ 1037.392208] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=68.84.148.164 DST=85.77.159.2 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=36964 DF PROTO=TCP SPT=38018 DPT=48209 WINDOW=8192 RES=0x00 SYN URGP=0 MARK=0x14 
Feb  1 22:10:43 Masiina modem-manager: CS registration state changed: 2
Feb  1 22:10:43 Masiina modem-manager: PS registration state changed: 2
Feb  1 22:10:43 Masiina modem-manager: CS registration state changed: 5
Feb  1 22:10:43 Masiina modem-manager: PS registration state changed: 5
Feb  1 22:19:34 Masiina kernel: imklog 4.2.0, log source = /proc/kmsg started.
```

---

### Post by runeh76 on 2011-02-02
REALLY strange, it happened AGAIN!
My net didnt work and i had to unplug 3G-dongle many times, then suddenly same freezing. Whats going on? Now im surfing again...BUT? 
By the way, now temperature shouldnt be a problem (got couple fans today)
Please answer how to solve this.

---

### Post by runeh76 on 2011-02-03
Double post  can be deleted

---

### Post by runeh76 on 2011-02-03
I guess the problem was my 3G MF668 usb dongle, becouse i got twice same hang and last hang was when i unplug/plug that dongle...
Got my (slow) DSL back now and that MF668 didnt "wake up" doesnt work anymore.. Only red light. Dont know what to do with it, i did try plug it to another computer, but same thing.
Could there be a firmware problem or similar?

---

### Post by [Snc] on 2011-02-03
Hey!, sorry for the late post ;)

Here is some info on this forum about your 3G usb stick [http://ubuntuforums.org/showthread.php?t=1396257](http://ubuntuforums.org/showthread.php?t=1396257)

(I haven't had the time to read it, but it's about the USB thing you have mentioned)

In the first code section, i noticed "Clocksource tsc unstable", when I googled this, i got a lot of hits about sudden kernel panics etc, after updating the kernel to a newer version. On the other hand, some results indicated system clock instability, which is a hardware problem... try searching in that direction...

PS. If temperature is the problem, for starters you could remove the cover from the computer, that should bring temperature down.

---

### Post by runeh76 on 2011-02-04
Thx for the replies!

I got new MF668 stick and now net is working.
Dont know sure, but i think that old stick cause somehow that freezing and now everything is OK.

ps. Lets see how long this one works   ;)

---

### Post by runeh76 on 2011-02-04
> **'[Snc] said:**
> 

In the first code section, i noticed "Clocksource tsc unstable", 



Dont get anymore that. From BIOS, ACPI--> Disabled  :)

---

### Post by jre on 2011-02-05
Hey,

as I understand it, your problems are solved. I just want to hint you to the fact, that *some* problems with websurfing might be due to your moblock installation (moblock blocks certain traffic based on huge IP blocklists).

Greets
jre

---

