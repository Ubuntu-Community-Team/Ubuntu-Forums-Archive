---
title: "Shutting off under heavy network use"
date: 2011-06-05
forum: General Help
---

### Post by un4v41l48l3 on 2011-06-05
Ok so I've scoured the web and I can't seem to find anyone else having this issue. 


**The issue:**

Whenever my box is heavily using the internet, it seems to just wimp out. It shuts off and reboots.


**When it's happened:**[LIST=1]
[*]I first deduced the connection to the network connection when I was trying to set up the system. When I tried an upgrade after the first time I installed the system, it crashed, leaving me with broken packages and all kinds of mess. So I decided to start over, and since I then had the network set up, I used the install latest version feature in the installer. If failed again.  I battled issue this a couple of times before I opted to do updates in chunks instead of all at once. Success.
[*]Then I tried to download an entire website. You see, I had bought the computer to use as a test server for work. I ran wget, I believe. After a lot of recursive downloading, it decided to take another unauthorized break.
[*]Now, I've got a minecraft server running too. It's been working pretty nicely, until lately. I've got a cron job set up to backup the server files with dropbox. Bad, bad, bad. The computer started acting up again, shutting off and rebooting. I figured it was having a hard time uploading to dropbox while simultaneously serving up the game. I moved the cron job from hourly to daily, and haven't had issues all day. Great.
[*]Until late tonight. It did it again while we were playing. It's relentless. So I went through the whole process of assessing damage. Luckily no damage. Then I went ahead and ran the dropbox script that didn't get to run while I was performing diagnostics. Guess what happened? ](*,)
[/LIST]


**System Info:**[LIST]
[*]Dell Optiplex 745
[*](L)Ubuntu 11.04 -- Linux 2.6.38-generic (i686)
[*]2 G RAM
[*]2.8 GHz Dual-Core Pentium D
[*]Ethernet connection -- DSL at 3Mbps DL and 1.5Mbps UL (Supposedly. My tests show half that)
[*]No temperature sensors -- We try to keep the room around 76° F, but the garage below doesn't make it easy. Computer is sitting on the floor under a desk.
[*]Manual IP on my LAN
[/LIST]



Please, help me out if you have any ideas. As always, just ask if you need more info.

---

### Post by un4v41l48l3 on 2011-06-05
*bump*

---

### Post by un4v41l48l3 on 2011-06-08
So, I've been monitoring my CPU, and it's never runs that hard. It's got a pretty easy life. I also installed an extra fan and tried several positions. No luck. I even disconnected unused hardware, hoping to eliminate the possibility of power supply and/or heat issues.

I'm getting these kinds of messages right before it shuts off&#8230;

**/var/logs/kern.log**
```
Jun  8 15:02:45 SkilletServer kernel: [   13.328774] drm: registered panic notifier
Jun  8 15:02:45 SkilletServer kernel: [   13.329422] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Jun  8 15:02:45 SkilletServer kernel: [   14.131505] type=1400 audit(1307563364.807:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=501 comm="apparmor_parser"
Jun  8 15:02:45 SkilletServer kernel: [   14.132539] type=1400 audit(1307563364.811:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=501 comm="apparmor_parser"
Jun  8 15:02:45 SkilletServer kernel: [   14.133208] type=1400 audit(1307563364.811:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=501 comm="apparmor_parser"
Jun  8 15:02:45 SkilletServer kernel: [   14.134359] type=1400 audit(1307563364.811:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=502 comm="apparmor_parser"
Jun  8 15:02:45 SkilletServer kernel: [   14.135390] type=1400 audit(1307563364.811:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=502 comm="apparmor_parser"
Jun  8 15:02:45 SkilletServer kernel: [   14.136074] type=1400 audit(1307563364.815:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=502 comm="apparmor_parser"
Jun  8 15:02:45 SkilletServer kernel: [   14.713771] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  8 15:02:45 SkilletServer kernel: [   14.713843] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
Jun  8 15:02:45 SkilletServer kernel: [   14.713879] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jun  8 15:02:45 SkilletServer kernel: [   15.233732] type=1400 audit(1307563365.911:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=600 comm="apparmor_parser"
Jun  8 15:02:45 SkilletServer kernel: [   15.235024] type=1400 audit(1307563365.911:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=599 comm="apparmor_parser"
Jun  8 15:02:48 SkilletServer kernel: [   17.611782] type=1400 audit(1307563368.287:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=705 comm="apparmor_parser"
Jun  8 15:02:48 SkilletServer kernel: [   17.613152] type=1400 audit(1307563368.291:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=705 comm="apparmor_parser"
Jun  8 15:02:51 SkilletServer kernel: [   21.167369] tg3 0000:03:00.0: irq 45 for MSI/MSI-X
Jun  8 15:02:51 SkilletServer kernel: [   21.200179] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun  8 15:02:52 SkilletServer kernel: [   21.444718] type=1400 audit(1307563372.123:12): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=758 comm="apparmor_parser"
Jun  8 15:02:52 SkilletServer kernel: [   21.445768] type=1400 audit(1307563372.123:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=758 comm="apparmor_parser"
Jun  8 15:02:52 SkilletServer kernel: [   21.446430] type=1400 audit(1307563372.123:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=758 comm="apparmor_parser"
Jun  8 15:02:52 SkilletServer kernel: [   21.452381] type=1400 audit(1307563372.131:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=760 comm="apparmor_parser"
Jun  8 15:02:52 SkilletServer kernel: [   21.453597] type=1400 audit(1307563372.131:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=760 comm="apparmor_parser"
Jun  8 15:02:52 SkilletServer kernel: [   21.567099] type=1400 audit(1307563372.243:17): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=761 comm="apparmor_parser"
Jun  8 15:02:52 SkilletServer kernel: [   21.571746] type=1400 audit(1307563372.247:18): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=763 comm="apparmor_parser"
Jun  8 15:02:52 SkilletServer kernel: [   21.826801] type=1400 audit(1307563372.503:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=759 comm="apparmor_parser"
Jun  8 15:02:52 SkilletServer kernel: [   21.840976] type=1400 audit(1307563372.519:20): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=759 comm="apparmor_parser"
Jun  8 15:02:52 SkilletServer kernel: [   21.849351] type=1400 audit(1307563372.527:21): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=759 comm="apparmor_parser"
Jun  8 15:02:53 SkilletServer kernel: [   22.840734] tg3 0000:03:00.0: eth0: Link is up at 100 Mbps, full duplex
Jun  8 15:02:53 SkilletServer kernel: [   22.840741] tg3 0000:03:00.0: eth0: Flow control is off for TX and off for RX
Jun  8 15:02:53 SkilletServer kernel: [   22.840911] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun  8 15:02:53 SkilletServer kernel: [   23.220801] device eth0 entered promiscuous mode
Jun  8 15:03:04 SkilletServer kernel: [   33.392017] eth0: no IPv6 routers present

```

I tried replacing the ethernet cord. I saw this is a common solution to "ADDRCONF(NETDEV_UP): eth0: link is not ready." But still no luck. It just crashed again.

---

