---
title: "Random freezing playing games"
date: 2012-08-02
forum: General Help
---

### Post by rendo on 2012-08-02
It's late and I apologize if this has been mentioned somewhere before.  Ever since I upgraded to 12.04, anytime I'm playing a game for an extended period of time (1-3 hours) my entire screen will freeze, the mouse can move around, I can't alt-tab out of the window, I can't change TTY's to kill programs.  Everything seems to be running fine in the background.  I was in a Skype call when it happened.  

At first I thought it was Wine, but it happened for Minecraft as well.  I thought it may have been Skype, but it still happens and it's becoming such an annoyance that I'm fed up with 12.04.  This _NEVER_ happened with 11.10.  I don't even know where to begin.  I can't tell if it's hardware, which I doubt since it all worked before, some setting I have, or what.

I'm computer savvy, but not Linux savvy.  I can follow tutorials and guides no problem.  Any help would be appreciated on how I can pinpoint the cause, how I can resolve it so I can move forward.  Any information needed I'll give.  Thanks.

---

### Post by 2F4U on 2012-08-02
Have you looked into the system log file if there are any problems reported? What are your hardware specs?

---

### Post by rendo on 2012-08-02
There's nothing in the syslog that I can see.  I would assume it'd be something blatant and obvious.

Specs
Mobo: Gigabyte GA-970A-D3
CPU: AMD FX(tm)-4100 Quad-Core Processor
RAM: 8Gigs Corsair something :P
GPU: GeForce 9600 GSO
HDD: WesterDigital 750GB WD7500AADS

---

### Post by rendo on 2012-08-02
So I just had another one so I copied parts of the syslog to list in here.  Perhaps someone with more knowledge will be able to see if there's anything out of the ordinary.

Aug  2 14:17:01 Rendo-personal CRON[15688]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug  2 14:18:43 Rendo-personal kernel: [48300.672546] delay: estimated 133, actual 0
Aug  2 14:19:33 Rendo-personal kernel: [48350.369288] delay: estimated 134, actual 1
Aug  2 14:19:37 Rendo-personal kernel: [48354.465441] delay: estimated 133, actual 0
Aug  2 14:19:42 Rendo-personal kernel: [48359.312148] delay: estimated 133, actual 1
Aug  2 14:21:03 Rendo-personal kernel: [48439.821832] delay: estimated 90, actual 1
Aug  2 14:21:07 Rendo-personal kernel: [48444.173496] delay: estimated 134, actual 1
Aug  2 14:22:08 Rendo-personal kernel: [48505.408116] delay: estimated 133, actual 0
Aug  2 14:34:02 Rendo-personal kernel: [49217.243719] delay: estimated 90, actual 1
Aug  2 14:37:49 Rendo-personal kernel: imklog 5.8.6, log source = /proc/kmsg started.
Aug  2 14:37:49 Rendo-personal rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="894" x-info="http://www.rsyslog.com"] start
Aug  2 14:37:49 Rendo-personal rsyslogd: rsyslogd's groupid changed to 103
Aug  2 14:37:49 Rendo-personal rsyslogd: rsyslogd's userid changed to 101
Aug  2 14:37:49 Rendo-personal rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Aug  2 14:37:49 Rendo-personal NetworkManager[940]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Aug  2 14:37:49 Rendo-personal NetworkManager[940]: <info> DNS: loaded plugin dnsmasq
Aug  2 14:37:49 Rendo-personal dbus[905]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Aug  2 14:37:49 Rendo-personal polkitd[961]: started daemon version 0.104 using authority implementation `local' version `0.104'
Aug  2 14:37:49 Rendo-personal dbus[905]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Aug  2 14:37:49 Rendo-personal NetworkManager[940]:    SCPlugin-Ifupdown: init!
Aug  2 14:37:49 Rendo-personal NetworkManager[940]:    SCPlugin-Ifupdown: update_system_hostname
Aug  2 14:37:49 Rendo-personal NetworkManager[940]:    SCPluginIfupdown: management mode: unmanaged
Aug  2 14:37:49 Rendo-personal NetworkManager[940]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:09.0/0000:03:00.0/net/eth1, iface: eth1)
Aug  2 14:37:49 Rendo-personal NetworkManager[940]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:09.0/0000:03:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Aug  2 14:37:49 Rendo-personal NetworkManager[940]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug  2 14:37:49 Rendo-personal kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug  2 14:37:49 Rendo-personal kernel: [    0.000000] Initializing cgroup subsys cpu

Everything after that appears to be the system loading everything to start up.  Hopefully this helps someone pinpoint the issue.  :(

---

