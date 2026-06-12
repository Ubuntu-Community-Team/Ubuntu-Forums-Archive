---
title: "Crashing, followed by fstab error."
date: 2009-10-31
forum: General Help
---

### Post by kircher on 2009-10-31
Hi all.

**Edit: I am almost certain this is caused by wpa_supplicant spamming the system with scans. Look at my later posts.**

I upgraded to 9.10 from 9.04 on Friday, and so far it has been the best release yet since I began using Ubuntu Breezy Badger (5.10). For the first time everything has 'just worked' without any fiddling. Even my USB wireless adapter works flawlessly which was a slight pain with 9.04. I am very happy with the performance so far.

So, apart from everything I'm happy about, there is a problem I have been encountering with the system freezing quite regularly. Since Friday the system has frozen approximately 5 times. In each case the mouse cursor was still movable, but I could not interact at all with my desktop environment, so was forced to do a manual restart of the system. In hindsight I probably should have checked whether it was just the X Window System that had crashed and tried to get into a Virtual Terminal, and restarted gdm. After my manual restart I was prompted with the message:
> One or more of the mounts listed in /etc/fstab cannot yet be mounted
/home: waiting for dev/disk/by....
and that is all I could write down before the system started up normally without a hitch.

It mentioned that both /home and /home/james/Music (my music partition) could not be mounted correctly. I have / and /home/james/Music on one hard drive and /home on a separate hard drive. This has not been a problem before.

Some more background information:
Motherboard - acer s88m: [[COLOR="Blue"]_motherboard specifications_[/COLOR]]("http://www.fixya.com/support/t2287474-acer_s88m_motherboard_find_real_manual")
processor - 1.7GHz celeron
memory - 1GB ddr 2700 ram
onboard graphics
onboard sound

40GB hard drive:
/ partition ext4
/home/james/Music partition ext3
swap partition (1GB)

320GB hard drive:
/home partition ext3

My first thoughts were that the problem could have something to do with the /home and /home/james/Music partitions crashing because the / partition is using ext4. Now I'm thinking that I'm only getting that particular error message because I was manually restarting the computer. I have since editied fstab so that / is mounted as ext3, rather than ext4, and I have so far had no problems and no more crashing, but that was only an hour or two ago. Does anyone else have any insight into what my problems may be or if they can direct me to other threads with similar issues? My own search found there were people having problems with a similar error message, but it was the swap partition that wasn't mounting.

Thanks for any assistance/insight

Kircher

---

### Post by kircher on 2009-10-31
I just encountered another system crash, which I had to resolve by restarting manually again, so mounting my ext4 / as ext3 didn't help.

---

### Post by capscrew on 2009-11-01
> **kircher said:**
> ...there is a problem I have been encountering with the system freezing quite regularly. ...After my manual restart I was prompted with the message:```
One or more of the mounts listed in /etc/fstab cannot yet be mounted
/home: waiting for dev/disk/by.... 
```

and that is all I could write down before the system started up normally without a hitch.

I believe that part you missed was ```
/home: waiting for dev/disk/by **UUID**
```

Post your /etc/fstab file.  The entries should be listed by UUID like this```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
[COLOR="Navy"]UUID=c2ff646e-4884-4c77-ab85-e8e958f1422b[/COLOR] /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda3
[COLOR="DarkGreen"]UUID=223b331e-418a-4bb1-b86e-b0c2b28abc03[/COLOR] /home           ext3    defaults        0       2
#
# /dev/sda4 !! manually added
[COLOR="Purple"]UUID=d49556bd-a3d7-4c5a-a87d-4679db6817f3[/COLOR] 	/smb		ext3	defaults0	2
# /dev/sda2
[COLOR="DarkSlateGray"]UUID=f21ea669-94b0-4df5-bc93-b948fa986177[/COLOR] none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

---

### Post by kircher on 2009-11-01
Yeah, that's what I didn't have time to write down. The missing parts would be something like: - 

> 
/home: waiting for /dev/disk/by UUID.....

/home/james/Music: waiting for /dev/disk/by UUID.....


This is my fstab file:
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=8f3783f5-1ab1-40cc-be4e-c0bc4f917a52 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=8250cecc-e124-4979-b91a-19e28cfe3a1f /home           ext3    defaults        0       2
# /home/james/Music was on /dev/sda4 during installation
UUID=a46540fa-eba9-49ff-ad3a-716b3ee984c0 /home/james/Music ext3    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=823c1c63-3955-4650-ba73-254e27beea92 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Note that /dev/sda1 is an ext4 partition, but I've edited fstab to mount it as an ext3. This however did not help.

The computer crashed again recently, and I tried to ctrl-alt-<function key> into a virtual console, but it seems it was completely frozen, apart from the visible mouse cursor movement.

---

### Post by capscrew on 2009-11-01
> **kircher said:**
> Yeah, that's what I didn't have time to write down...

Note that /dev/sda1 is an ext4 partition, but I've edited fstab to mount it as an ext3. This however did not help.

I would return the mount to the FS type that the partition really is (e.g. Ext4 if that is what it is).> 

The computer crashed again recently, and I tried to ctrl-alt-<function key> into a virtual console, but it seems it was completely frozen, apart from the visible mouse cursor movement.

I would check the log files for data.  What do you get in dmesg or the syslog?  I now I'm not much help.  I will say that you are not the 1st person to have this exact problem.  Maybe you can report a bug.  I think it is deeper than just a misconfiguration.

Check out [_[COLOR="DarkSlateGray"]this[/COLOR]_]("http://www.ubuntu.com/community/ReportProblem") for how to report bugs.

---

### Post by kircher on 2009-11-01
You mentioned that others are having this exact problem. Is there a thread dedicated to this specifically? I am reluctant to file a bug report because I have inadequate information about what is actually happening. I do have another idea. Every time the system has crashed I have had Firefox open. Is it possible it's linked to Firefox? It is possible it's not related to Firefox at all, because I always have Firefox open. So I can't exactly compare it to incidences when I am not using Firefox

The contents of /var/log/kern.log don't give any mention to what I am looking for, but I don't exactly know what I am looking for either. It's huge, so I'll attach it a text file rather than in here as text.

I had another crash while I was writing this post as well.

Thanks for your help. It is kind of reassuring to know that it's not an isolated problem.

---

### Post by kircher on 2009-11-01
Ok, I had another crash about an hour and a half ago, and I didn't turn the computer back on after manually shutting down until about 20 minutes ago. I looked through /var/log/syslog and found the point where the last log entry was entered. I highlighted the last entry and the first entry of the current session.
> Nov  1 20:25:03 desktop NetworkManager: <info>  Policy set 'orgolf' (wlan0) as default for routing and DNS.
Nov  1 20:25:03 desktop NetworkManager: <info>  Activation (wlan0) successful, device activated.
Nov  1 20:25:03 desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Nov  1 20:25:05 desktop ntpdate[2655]: adjust time server 91.189.94.4 offset 0.249104 sec
Nov  1 20:25:09 desktop kernel: [ 2437.544055] wlan0: no IPv6 routers present
Nov  1 20:25:16 desktop wpa_supplicant[1158]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 20:25:56 desktop wpa_supplicant[1158]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 20:26:54 desktop wpa_supplicant[1158]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 20:28:14 desktop wpa_supplicant[1158]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 20:29:54 desktop wpa_supplicant[1158]: CTRL-EVENT-SCAN-RESULTS 
[COLOR="Red"]Nov  1 20:31:54 desktop wpa_supplicant[1158]: CTRL-EVENT-SCAN-RESULTS[/COLOR] 
[COLOR="Lime"]Nov  1 21:42:45 desktop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.[/COLOR]
Nov  1 21:42:45 desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="747" x-info="http://www.rsyslog.com"] (re)start
Nov  1 21:42:45 desktop rsyslogd: rsyslogd's groupid changed to 102
Nov  1 21:42:45 desktop rsyslogd: rsyslogd's userid changed to 101
Nov  1 21:42:45 desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  1 21:42:45 desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  1 21:42:45 desktop kernel: [    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
Nov  1 21:42:45 desktop kernel: [    0.000000] KERNEL supported cpus:
Nov  1 21:42:45 desktop kernel: [    0.000000]   Intel GenuineIntel
Nov  1 21:42:45 desktop kernel: [    0.000000]   AMD AuthenticAMD
Nov  1 21:42:45 desktop kernel: [    0.000000]   NSC Geode by NSC
Nov  1 21:42:45 desktop kernel: [    0.000000]   Cyrix CyrixInstead
Nov  1 21:42:45 desktop kernel: [    0.000000]   Centaur CentaurHauls
Nov  1 21:42:45 desktop kernel: [    0.000000]   Transmeta GenuineTMx86
Nov  1 21:42:45 desktop kernel: [    0.000000]   Transmeta TransmetaCPU
Nov  1 21:42:45 desktop kernel: [    0.000000]   UMC UMC UMC UMC
Nov  1 21:42:45 desktop kernel: [    0.000000] BIOS-provided physical RAM

The last /var/log/kern.log entry of the last session that froze was at 20:25:09, which is approximately 7 minutes before the last /var/log/syslog entry was made, so I think I can assume there is no useful information in kern.log. The last syslog entries are related to my wireless network connection. Is it possible there is a problem with the wireless drivers or some other software issue related to the wireless internet? or related to the wpa supplicant as listed in the log? In particular, what does "**desktop wpa_supplicant[1158]: CTRL-EVENT-SCAN-RESULTS**" mean? Is 1158 a process ID? It's not listed in my system monitor as a running process? Is that because it's a daemon?

---

### Post by kircher on 2009-11-01
My system just crashed again, and I checked the log: /var/log/syslog again after restarting. I think it confirms that wpa_supplicant is causing the problems with its constant scanning right up until the actual crash. Here are the relevant contents of the log, again with the last entry before the crash highlighted in red, and the first after restarting in green:
> Nov  1 22:10:01 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:12:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:14:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:15:22 desktop pulseaudio[1524]: ratelimit.c: 126 events suppressed
Nov  1 22:15:55 desktop pulseaudio[1524]: ratelimit.c: 117 events suppressed
Nov  1 22:16:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:16:22 desktop pulseaudio[1524]: ratelimit.c: 67 events suppressed
Nov  1 22:17:01 desktop CRON[2182]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  1 22:17:06 desktop pulseaudio[1524]: ratelimit.c: 10 events suppressed
Nov  1 22:18:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:20:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:22:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:24:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:26:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:28:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:30:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:32:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:34:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:36:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:38:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:40:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:42:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 22:44:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS 
[COLOR="Red"]Nov  1 22:46:00 desktop wpa_supplicant[1156]: CTRL-EVENT-SCAN-RESULTS[/COLOR] 
[COLOR="SeaGreen"]Nov  1 22:49:41 desktop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.[/COLOR]
Nov  1 22:49:41 desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="740" x-info="http://www.rsyslog.com"] (re)start
Nov  1 22:49:41 desktop rsyslogd: rsyslogd's groupid changed to 102
Nov  1 22:49:41 desktop rsyslogd: rsyslogd's userid changed to 101
Nov  1 22:49:41 desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  1 22:49:41 desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  1 22:49:41 desktop kernel: [    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
Nov  1 22:49:41 desktop kernel: [    0.000000] KERNEL supported cpus:
Nov  1 22:49:41 desktop kernel: [    0.000000]   Intel GenuineIntel
Nov  1 22:49:41 desktop kernel: [    0.000000]   AMD AuthenticAMD
Nov  1 22:49:41 desktop kernel: [    0.000000]   NSC Geode by NSC
Nov  1 22:49:41 desktop kernel: [    0.000000]   Cyrix CyrixInstead

Someone else has filed a bug report with the same problem. Here are the details [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1799427.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1799427.html)

What should I do? file a new bug report or can I comment on that one?

---

### Post by kircher on 2009-11-01
I just had another crash/freeze and once again the syslog confirms that wpa_supplicant is the culprit.

---

### Post by kircher on 2009-11-01
I filed a bug report. Here it is: [https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/468519](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/468519)

---

