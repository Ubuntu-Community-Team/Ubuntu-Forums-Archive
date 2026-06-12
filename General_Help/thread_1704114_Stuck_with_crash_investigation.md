---
title: "Stuck with crash investigation"
date: 2011-03-10
forum: General Help
---

### Post by Hawkoon on 2011-03-10
My laptop had crashed when I returned this morning. The screen was turned off (as it always does due to screensaver settings), fan still spinning as usual, no response to the keyboard so I couldn't bring the screen back on. I couldn't even ssh into it (I use this laptop to try out server stuff like apache, nfs, mt-daap, ftp) so I had no choice but restart the system by powering off and back on.

I'd like to know why the laptop crashed and looked at syslog

```
Mar 10 01:03:30 sun kernel: [229210.432809] [UFW AUDIT] IN=wlan0 OUT= MAC=00:0b:cd:5c:e3:4b:00:1f:3f:64:f2:69:08:00 SRC=110.174.225.152 DST=192.168.2.104$
Mar 10 01:03:30 sun kernel: [229210.432910] [UFW BLOCK] IN=wlan0 OUT= MAC=00:0b:cd:5c:e3:4b:00:1f:3f:64:f2:69:08:00 SRC=110.174.225.152 DST=192.168.2.104$
Mar 10 01:03:33 sun kernel: [229213.479578] [UFW BLOCK] IN=wlan0 OUT= MAC=00:0b:cd:5c:e3:4b:00:1f:3f:64:f2:69:08:00 SRC=110.174.225.152 DST=192.168.2.104$
Mar 10 01:03:39 sun kernel: [229219.516910] [UFW AUDIT] IN=wlan0 OUT= MAC=00:0b:cd:5c:e3:4b:00:1f:3f:64:f2:69:08:00 SRC=110.174.225.152 DST=192.168.2.104$
Mar 10 01:03:39 sun kernel: [229219.517009] [UFW BLOCK] IN=wlan0 OUT= MAC=00:0b:cd:5c:e3:4b:00:1f:3f:64:f2:69:08:00 SRC=110.174.225.152 DST=192.168.2.104$
Mar 10 01:03:47 sun kernel: [229227.532206] [UFW AUDIT] IN= OUT=wlan0 SRC=192.168.2.104 DST=50.72.33.94 LEN=131 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=U$
Mar 10 01:03:47 sun kernel: [229227.532251] [UFW ALLOW] IN= OUT=wlan0 SRC=192.168.2.104 DST=50.72.33.94 LEN=131 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=U$
Mar 10 01:03:48 sun mt-daapd[1503]: Write error: Connection reset by peer
Mar 10 01:03:50 sun kernel: [229230.681293] [UFW BLOCK] IN=wlan0 OUT= MAC=00:0b:cd:5c:e3:4b:00:1f:3f:64:f2:69:08:00 SRC=78.145.139.27 DST=192.168.2.104 L$
Mar 10 01:03:56 sun mt-daapd[1503]: Write error: Connection reset by peer
Mar 10 01:03:56 sun kernel: [229236.977090] [UFW AUDIT] IN=wlan0 OUT= MAC=00:0b:cd:5c:e3:4b:00:22:43:15:48:cf:08:00 SRC=192.168.2.105 DST=192.168.2.104 L$
Mar 10 01:03:59 sun mt-daapd[1503]: Write error: Connection reset by peer
Mar 10 01:04:05 sun mt-daapd[1503]: Write error: Connection reset by peer
Mar 10 01:04:12 sun kernel: [229252.908212] [UFW AUDIT] IN= OUT=wlan0 SRC=192.168.2.104 DST=82.19.214.99 LEN=131 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=$
Mar 10 01:04:12 sun kernel: [229252.908238] [UFW ALLOW] IN= OUT=wlan0 SRC=192.168.2.104 DST=82.19.214.99 LEN=131 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=$
Mar 10 09:15:29 sun kernel: imklog 4.2.0, log source = /proc/kmsg started.
Mar 10 09:15:29 sun rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="831" x-info="http://www.rsyslog.com"] (re)start
Mar 10 09:15:29 sun rsyslogd: rsyslogd's groupid changed to 103
Mar 10 09:15:29 sun rsyslogd: rsyslogd's userid changed to 101
Mar 10 09:15:29 sun rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Mar 10 09:15:29 sun kernel: [    0.000000] Initializing cgroup subsys cpuset
```but the only thing I can learn from there is that the crash must have occurred around 01:04:12, and that mt-daapd was serving music.

The mt-daapd log doesn't show anything suspicious either
```

2011-03-10 01:03:48 (b5921b70): Write error: Connection reset by peer
2011-03-10 01:03:48 (b5921b70): Session 0: Streaming file '12 Blue Suede Shoes.mp3' to 192.168.2.105 (offset 0)
2011-03-10 01:03:56 (b5921b70): Write error: Connection reset by peer
2011-03-10 01:03:56 (b5921b70): Session 0: Streaming file '12 The Reflex.mp3' to 192.168.2.105 (offset 0)
2011-03-10 01:03:59 (b5921b70): Write error: Connection reset by peer
2011-03-10 01:04:02 (b4f20b70): Session 0: Streaming file '06 Something To Remember.mp3' to 192.168.2.105 (offset 0)
2011-03-10 01:04:05 (b4f20b70): Write error: Connection reset by peer
2011-03-10 01:04:08 (b5921b70): Session 0: Streaming file '13 Boston Belongs To Me.mp3' to 192.168.2.105 (offset 0)
2011-03-10 09:15:47 (b78366d0): Firefly Version svn-1696: Starting with debuglevel 2
2011-03-10 09:15:47 (b78366d0): Error loading plugin /usr/lib/mt-daapd/plugins/ssc-script.so: plugin declined to load
2011-03-10 09:15:47 (b78366d0): Plugin loaded: daap/svn-1696
2011-03-10 09:15:47 (b78366d0): Plugin loaded: ssc-ffmpeg/svn-1696
2011-03-10 09:15:47 (b78366d0): Plugin loaded: rsp/svn-1696
2011-03-10 09:15:47 (b78366d0): Starting signal handler
2011-03-10 09:15:47 (b78366d0): Starting rendezvous daemon
2011-03-10 09:15:47 (b78366d0): Client running
2011-03-10 09:15:47 (b78366d0): Initializing database
```What else can I do to investigate this crash further? I found some guides on investigating crashes but they all seem quite specific, like debugging X freezes. How do you proceed if you have no idea what part of the system failed?

---

