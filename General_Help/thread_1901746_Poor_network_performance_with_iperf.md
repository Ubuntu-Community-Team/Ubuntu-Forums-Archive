---
title: "Poor network performance with iperf"
date: 2011-12-29
forum: General Help
---

### Post by jugglingcats on 2011-12-29
Hi, am running Ubuntu 10.04 on ASUS AT3IONT-I DELUXE (Atom 330) motherboard in a home network. I recently created a Windows 7 share for movies in order to stream to the Ubuntu machine (running MythTV).

When streaming ISOs or other high bitrate files we notice buffering. The network is 100BaseT. The router shows 100mbps full duplex for both machines (Windows 7 server and Ubuntu client).

iperf from Ubuntu shows the following:

```

------------------------------------------------------------
Client connecting to 192.168.1.3, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.14 port 44326 connected with 192.168.1.3 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  5.02 MBytes  4.21 Mbits/sec
[  3] 10.0-20.0 sec  6.24 MBytes  5.24 Mbits/sec
[  3] 20.0-30.0 sec  6.92 MBytes  5.81 Mbits/sec
[  3] 30.0-40.0 sec  12.7 MBytes  10.7 Mbits/sec
[  3] 40.0-50.0 sec  10.3 MBytes  8.66 Mbits/sec

```

These figures are much lower than I would expect and also show more variation (highest figure is more than twice the lowest figure).

I originally thought this was probably a CIFs issue (lots of threads on that), but iperf is not doing well either as you can see.

Any suggestions? I could upgrade to a gigabit router, as both machines are gigabit capable, but I shouldn't really need to and am worried it won't make much difference if the Atom machine is I/O or CPU bound somehow or it's a Ubuntu config/tuning issue.

Any help much appreciated!

Alfie.

---

### Post by gordintoronto on 2011-12-29
Are you streaming to video? If so, you would probably get much better performance with a faster CPU and an Nvidia video card with VDPau installed. Oh, that motherboard has Nvidia graphics; did you install VDPau? (Also mplayer2 and smplayer. In smplayer, go into options> preferences> video> output driver, select vdpau.)

You could try a lightweight version of Ubuntu such as Lubuntu or Xubuntu.

See also: [http://www.mythtv.org/wiki/Optimizing_Performance](http://www.mythtv.org/wiki/Optimizing_Performance)

---

### Post by jugglingcats on 2011-12-29
Thanks for the reply. This is more of a networking issue - video performance with the NVidia ION chipset is good. Playing back video stored locally is fine - even at 1080. Only streaming over the local LAN is a problem.

---

### Post by jugglingcats on 2011-12-30
Been experimenting a bit with this today. I connected up an old XP laptop and tried iperf from Ubuntu with XP as the server and am consistently getting 93mbps through the hub. This indicates my Windows 7 server is the bottleneck which is strange since it's relatively new (2 yrs old).

Not an ubuntu issue so feel free to ignore - but any suggestions on where to look next appreciated!

---

### Post by jugglingcats on 2011-12-30
Tracked this down to Carbonite online backup. Pause the backup all good, resume the backup and poor performance.

Am surprised as the throughput on the upstream ADSL will be tiny compared to the local LAN and it shouldn't really affect local LAN anyway...

But at least I have a reason and workaround!

---

