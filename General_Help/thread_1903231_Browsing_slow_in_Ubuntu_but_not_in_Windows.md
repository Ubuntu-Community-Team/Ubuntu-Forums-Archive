---
title: "Browsing slow in Ubuntu but not in Windows"
date: 2012-01-02
forum: General Help
---

### Post by jcd29 on 2012-01-02
A few days ago my browsing speed in Ubuntu slowed down to a crawl. Every page takes forever to load, especially when I open Chromium or Firefox with a lot of tabs to load. I did a bunch of speed tests and it all came back normal.

Windows still has the same browsing speed as always.

What could be happening?

---

### Post by jcd29 on 2012-01-02
Did another test: Connected directly to my modem to rule out my router being the problem, but it's still slow.

---

### Post by pretty_whistle on 2012-01-02
Have you tried shutting the computer off, pulling out the battery if it's a laptop, wait 30 seconds, then power it back up?

I saw this in another thread as a solution.

---

### Post by crazy bird on 2012-01-02
If you are connected directly to your modem/router and surfing under Ubuntu still sucks but Windows is okay, the cause of the problem migth be switching from Windows to Ubuntu. I know there was something you had to do in Windows to make the network connection under Ubuntu as it should be. I am at work rigth now, but at home i have a script which has to be run under Windows.

---

### Post by crazy bird on 2012-01-02
Okay, i found the file i spoke about above. It's a file which need to be used under Windows. The following steps needs to be done under Windows:

[LIST]
[*]In windows, open notepad
[*]Type the following line in the empty file: **&#65279;[COLOR=DarkRed]ipconfig /release[/COLOR]**
[*]save the file to the desktop, keep in mind that the extension of the file must be **.cmd**
[/LIST]
When you want to log out of Windows, doubleclick this file first to release the network connection. If everything goed alrigth, you won't have any problems under Ubuntu with your network connection.

---

### Post by jcd29 on 2012-01-02
> **pretty_whistle said:**
> Have you tried shutting the computer off, pulling out the battery if it's a laptop, wait 30 seconds, then power it back up?

I saw this in another thread as a solution.
It's a desktop.
> **crazy bird said:**
> If you are connected directly to your modem/router and surfing under Ubuntu still sucks but Windows is okay, the cause of the problem migth be switching from Windows to Ubuntu. I know there was something you had to do in Windows to make the network connection under Ubuntu as it should be. I am at work rigth now, but at home i have a script which has to be run under Windows.
The thing is, I never use Windows. I've had Ubuntu 11.04 for quite a few months now and my browsing speed has been just fine. Then all of a sudden it slowed down to a crawl. After a day I booted into Windows to test it out and see if I had the same problem there and noticed the speeds were just fine there.

So I don't know if it's really a Windows problem if it's not a partition I boot into at all really.

---

### Post by crazy bird on 2012-01-02
> **jcd29 said:**
> 
So I don't know if it's really a Windows problem if it's not a partition I boot into at all really.
But you did boot into Windows? Just give that .cmd command thing a try. You never know

---

### Post by jcd29 on 2012-01-02
Just tried it. 

Nothing, still the same problem :(

---

### Post by crazy bird on 2012-01-03
Can you teel us what kind of network interfaces you're using? Brand/model network cards, which protocol you're using (wifi) and such.

---

### Post by jcd29 on 2012-01-03
> **crazy bird said:**
> Can you teel us what kind of network interfaces you're using? Brand/model network cards, which protocol you're using (wifi) and such.

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0100] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.4 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 [8086:1c18] (rev b5)
00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b5)
00:1c.6 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 7 [8086:1c1c] (rev b5)
00:1c.7 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 8 [8086:1c1e] (rev b5)
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation P67 Express Chipset Family LPC Controller [8086:1c46] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller [8086:1c02] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:1244] (rev a1)
01:00.1 Audio device [0403]: nVidia Corporation Device [10de:0bee] (rev a1)
03:00.0 SATA controller [0106]: Marvell Technology Group Ltd. Device [1b4b:9120] (rev 12)
04:00.0 USB Controller [0c03]: Device [1b6f:7023] (rev 01)
05:00.0 USB Controller [0c03]: Device [1b6f:7023] (rev 01)
06:00.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:01.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:04.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:05.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:06.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:07.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:08.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:09.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
09:00.0 PCI bridge [0604]: Device [1b21:1080] (rev 01)
0b:00.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6315 Series Firewire Controller [1106:3403] (rev 01)
0c:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)

---

### Post by jcd29 on 2012-01-04
Any ideas? I don't get how it just happened all of a sudden.

---

### Post by lucazade on 2012-01-04
take a look at 'ifconfig' if there are dropped/malformed packets:

....
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
....


look also at kernel log for network driver issues:
dmesg | tail -n 20

---

### Post by jcd29 on 2012-01-04
Just hoping there's a solution and I don't have to reinstall.

---

### Post by jcd29 on 2012-01-04
> **lucazade said:**
> take a look at 'ifconfig' if there are dropped/malformed packets:

....
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
....


look also at kernel log for network driver issues:
dmesg | tail -n 20

ifconfig
...
          RX packets:5550445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5809480 errors:0 dropped:0 overruns:0 
...
          RX packets:1498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1498 errors:0 dropped:0 overruns:0 carrier:0
...


----


dmesg | tail -n 20
[38220.555715] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38220.661426] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38220.739448] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38224.153935] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38224.158456] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38224.270677] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38228.208310] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38228.286091] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38228.291148] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38228.384860] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38228.566939] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38228.992994] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38229.009403] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38229.188176] net_ratelimit: 2 callbacks suppressed
[38229.188181] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38271.953522] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38272.007532] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38357.898160] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38387.443014] r8169 0000:0c:00.0: eth0: link down
[38401.175045] r8169 0000:0c:00.0: eth0: link up

---

### Post by lucazade on 2012-01-05
> **jcd29 said:**
> ifconfig
...
          RX packets:5550445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5809480 errors:0 dropped:0 overruns:0 
...
          RX packets:1498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1498 errors:0 dropped:0 overruns:0 carrier:0
...


----


dmesg | tail -n 20
[38220.555715] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38220.661426] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38220.739448] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38224.153935] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38224.158456] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38224.270677] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38228.208310] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38228.286091] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38228.291148] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38228.384860] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38228.566939] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38228.992994] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38229.009403] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38229.188176] net_ratelimit: 2 callbacks suppressed
[38229.188181] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38271.953522] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38272.007532] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38357.898160] TCP: Possible SYN flooding on port 10891. Sending cookies.
[38387.443014] r8169 0000:0c:00.0: eth0: link down
[38401.175045] r8169 0000:0c:00.0: eth0: link up

[http://squid-web-proxy-cache.1019090.n4.nabble.com/possible-SYN-flooding-on-port-3128-Sending-cookies-td2242687.html](http://squid-web-proxy-cache.1019090.n4.nabble.com/possible-SYN-flooding-on-port-3128-Sending-cookies-td2242687.html)

there is something wrong in network drivers.. search for SYN flooding in google and try also to see if reproducible in livecd (without re- installing).

---

### Post by jcd29 on 2012-01-05
> **lucazade said:**
> [http://squid-web-proxy-cache.1019090.n4.nabble.com/possible-SYN-flooding-on-port-3128-Sending-cookies-td2242687.html](http://squid-web-proxy-cache.1019090.n4.nabble.com/possible-SYN-flooding-on-port-3128-Sending-cookies-td2242687.html)

there is something wrong in network drivers.. search for SYN flooding in google and try also to see if reproducible in livecd (without re- installing).

I ran it again today and got:


dmesg | tail -n 20
[   11.553309] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.553317] nvidia 0000:01:00.0: setting latency timer to 64
[   11.553328] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   11.553479] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  270.41.06  Mon Apr 18 14:53:56 PDT 2011
[   11.651728] vesafb: framebuffer at 0xd9000000, mapped to 0xffffc90013a80000, using 5120k, total 5120k
[   11.651730] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   11.651731] vesafb: scrolling: redraw
[   11.651732] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   11.651829] Console: switching to colour frame buffer device 160x64
[   11.651845] fb0: VESA VGA frame buffer device
[   11.672593] ppdev: user-space parallel port driver
[   11.711326] r8169 0000:0c:00.0: eth0: link up
[   11.711703] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   11.834536] ioremap error for 0xbf52f000-0xbf530000, requested 0x10, got 0x0
[   14.132006] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[   14.133256] EXT4-fs (sdb1): re-mounted. Opts: commit=0
[   15.355808] hda-intel: IRQ timing workaround is activated for card #2. Suggest a bigger bdl_pos_adj.
[  760.526650] exe (2057): /proc/2057/oom_adj is deprecated, please use /proc/2057/oom_score_adj instead.
[ 1177.477955] r8169 0000:0c:00.0: eth0: link down
[ 1206.783959] r8169 0000:0c:00.0: eth0: link up

---

### Post by jcd29 on 2012-01-05
I tried this fix:
[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

And nothing's different.

I also have Ipv6 disabled, and I'm using google's DNS servers.

I'll try booting with a live cd like you said.

---

### Post by lucazade on 2012-01-06
Try the livecd and search in the ubuntu forums for that network card issue.. is not the first time I read this issue for that realtek card but I've no direct experience with it.

---

### Post by jcd29 on 2012-01-06
Just tried the Live CD and everything worked fine there.

Not sure how to proceed now since I tried the network card driver fix and it didn't work.

---

### Post by topsites on 2012-01-07
Get some paper, a pen.

First on Live CD:
Click the little Gear on the top left and then System Settings and Network.
Once in that window Write down EVERYTHING!
Then click Configure and once again Write down EVERYTHING (and on every tab!)

Reboot into your regular version:
Now click the little gear and go to the same network thing and click through to everything and compare notes.
What it says vs. what you wrote down.

If anything is different, try and see if you can make your regular version the same as the Live CD.
Let us know.

---

### Post by jcd29 on 2012-01-07
Ok I just tried this, and the settings are both exactly the same.

---

### Post by jcd29 on 2012-01-09
Any others having this same problem?

---

### Post by malikge on 2012-01-09
Yes, 
I am having the same problem...

---

### Post by jcd29 on 2012-01-09
> **malikge said:**
> Yes, 
I am having the same problem...

Ubuntu 11.04? When did you first start experiencing this problem?

---

### Post by topsites on 2012-01-09
At this point I am guessing the problem is within Firefox itself, have you tried this:
[http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html](http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html)

---

### Post by jcd29 on 2012-01-09
> **topsites said:**
> At this point I am guessing the problem is within Firefox itself, have you tried this:
[http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html](http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html)

I'm actually using Chromium.

But I did try Firefox too, and it was still slow. (Opera too)

---

### Post by amendt on 2012-01-10
I am having the same problem, I tried re-installing Chromium, but that didn't help. I find that Firefox works fine for me, just not Chromium 14.??? Ubuntu 11.10 uses Chromium 15.0.874.106 and it works fine, so I am just waiting for a software update.

---

### Post by malikge on 2012-01-11
> **jcd29 said:**
> Ubuntu 11.04? When did you first start experiencing this problem?
 
I am having this problem in both 10.04 and 11.10.  This problem started the first day I installed Ubuntu 10.04.


I have also update kernel, but still no luck
But on Window 7 every thing works fine.

---

### Post by spacecheck on 2012-01-11
Have you tried clearing the browser cache ? How about looking through the list of extensions, add-ins or plug-ins, and disabling them individually, to see if the problem stops when a specific one is turned off?

If that doesn't help, you could perhaps run  a test with Berkley's [Netalyzr]("http://netalyzr.icsi.berkeley.edu/"), to see if it finds any connection problems.

If a suggestion solves the problem, use the thread tools to mark the thread Solved. If not solved, report back for further input.

Good luck!

---

### Post by jcd29 on 2012-01-11
> **spacecheck said:**
> Have you tried clearing the browser cache ? How about looking through the list of extensions, add-ins or plug-ins, and disabling them individually, to see if the problem stops when a specific one is turned off?

If that doesn't help, you could perhaps run  a test with Berkley's [Netalyzr]("http://netalyzr.icsi.berkeley.edu/"), to see if it finds any connection problems.

If a suggestion solves the problem, use the thread tools to mark the thread Solved. If not solved, report back for further input.

Good luck!
I've cleared the cache, even used Bleachbit. And I've also tried with Firefox and downloading Opera, but still the same problem.

Here's what I got with netalyzr:

> Summary of Noteworthy Events –
Major Abnormalities
Your ISP's DNS server is slow to lookup names 
Minor Aberrations
Certain TCP protocols are blocked in outbound traffic 
Network packet buffering may be excessive 
The NAT's DNS proxy doesn't fully implement the DNS standard 
Not all DNS types were correctly processed 
Address-based Tests +
NAT detection (?): NAT Detected
Local Network Interfaces (?): OK
DNS-based host information (?): OK
NAT support for Universal Plug and Play (UPnP) (?): Yes
Reachability Tests –
TCP connectivity (?): Note
Direct TCP access to remote FTP servers (port 21) is allowed.
Direct TCP access to remote SSH servers (port 22) is allowed.
Direct TCP access to remote SMTP servers (port 25) is allowed.
Direct TCP access to remote DNS servers (port 53) is allowed.
Direct TCP access to remote HTTP servers (port 80) is allowed.
Direct TCP access to remote POP3 servers (port 110) is allowed.
Direct TCP access to remote RPC servers (port 135) is blocked.
This is probably for security reasons, as this protocol is generally not designed for use outside the local network.
Direct TCP access to remote NetBIOS servers (port 139) is blocked.
This is probably for security reasons, as this protocol is generally not designed for use outside the local network.
Direct TCP access to remote IMAP servers (port 143) is allowed.
Direct TCP access to remote SNMP servers (port 161) is allowed.
Direct TCP access to remote HTTPS servers (port 443) is allowed.
Direct TCP access to remote SMB servers (port 445) is blocked.
This is probably for security reasons, as this protocol is generally not designed for use outside the local network.
Direct TCP access to remote SMTP/SSL servers (port 465) is allowed.
Direct TCP access to remote secure IMAP servers (port 585) is allowed.
Direct TCP access to remote authenticated SMTP servers (port 587) is allowed.
Direct TCP access to remote IMAP/SSL servers (port 993) is allowed.
Direct TCP access to remote POP/SSL servers (port 995) is allowed.
Direct TCP access to remote OpenVPN servers (port 1194) is allowed.
Direct TCP access to remote PPTP Control servers (port 1723) is allowed.
Direct TCP access to remote SIP servers (port 5060) is allowed.
Direct TCP access to remote BitTorrent servers (port 6881) is allowed.
Direct TCP access to remote TOR servers (port 9001) is allowed.
UDP connectivity (?): OK
Basic UDP access is available.
The applet was able to send fragmented UDP traffic.
The applet was able to receive fragmented UDP traffic.
Direct UDP access to remote DNS servers (port 53) is allowed.
Direct UDP access to remote NTP servers (port 123) is allowed.
Direct UDP access to remote NetBIOS NS servers (port 137) is blocked.
Direct UDP access to remote NetBIOS DGM servers (port 138) is blocked.
Direct UDP access to remote IKE key exchange servers (port 500) is allowed.
Direct UDP access to remote OpenVPN servers (port 1194) is allowed.
Direct UDP access to remote Slammer servers (port 1434) is allowed.
Direct UDP access to remote L2 tunneling servers (port 1701) is allowed.
Direct UDP access to remote IPSec NAT servers (port 4500) is allowed.
Direct UDP access to remote RTP servers (port 5004) is allowed.
Direct UDP access to remote RTCP servers (port 5005) is allowed.
Direct UDP access to remote SIP servers (port 5060) is allowed.
Direct UDP access to remote VoIP servers (port 7078) is allowed.
Direct UDP access to remote VoIP servers (port 7082) is allowed.
Direct UDP access to remote SCTP servers (port 9899) is allowed.
Direct UDP access to remote Steam gaming servers (port 27005) is allowed.
Direct UDP access to remote Steam gaming servers (port 27015) is allowed.
Traceroute (?): OK
It takes 11 network hops for traffic to pass from our server to your system, as shown below. For each hop, the time it takes to traverse it is shown in parentheses.
10.254.184.3 (0 ms)
ip-10-1-16-1.ec2.internal (0 ms)
ip-10-1-17-14.ec2.internal (0 ms)
216.182.224.78 (0 ms)
72.21.222.148 (0 ms)
72.21.220.68 (1 ms)
64.211.194.153 (1 ms)
lag9.csr2.DCA3.gblx.net (9 ms)
cm-200-75-201-202.cpe-statics.cableonda.net (62 ms)
64.215.185.74 (74 ms)
cpe-0014bf854429.cpe.cableonda.net (69 ms)
Path MTU (?): OK
The path between your network and our system supports an MTU of at least 1500 bytes, and the path between our system and your network has an MTU of 1500 bytes.
Network Access Link Properties –
Network latency measurements (?): Latency: 78ms Loss: 0.0%
The round-trip time (RTT) between your computer and our server is 78 msec, which is good.
We recorded no packet loss between your system and our server.
TCP connection setup latency (?): 77ms
The time it takes your computer to set up a TCP connection with our server is 77 msec, which is good.
Network background health measurement (?): no transient outages
During most of Netalyzr's execution, the applet continuously measures the state of the network in the background, looking for short outages. During testing, the applet observed no such outages.
Network bandwidth measurements (?): Upload 1010 Kbit/sec, Download 4.1 Mbit/sec
Your Uplink: We measured your uplink's sending bandwidth at 1010 Kbit/sec. This level of bandwidth works well for many users. 
During this test, the applet observed 61 reordered packets.
Your Downlink: We measured your downlink's receiving bandwidth at 4.1 Mbit/sec. This level of bandwidth works well for many users. 
During this test, the applet observed 682 reordered packets.
Network buffer measurements (?): Uplink 550 ms, Downlink 590 ms
We estimate your uplink as having 550 msec of buffering. This level can in some situations prove somewhat high, and you may experience degraded performance when performing interactive tasks such as web-surfing while simultaneously conducting large uploads. Real-time applications, such as games or audio chat, may also work poorly when conducting large uploads at the same time.
We estimate your downlink as having 590 msec of buffering. This level can in some situations prove somewhat high, and you may experience degraded performance when performing interactive tasks such as web-surfing while simultaneously conducting large downloads. Real-time applications, such as games or audio chat, may also work poorly when conducting large downloads at the same time.
HTTP Tests +
Address-based HTTP proxy detection (?): OK
Content-based HTTP proxy detection (?): OK
HTTP proxy detection via malformed requests (?): OK
Filetype-based filtering (?): OK
HTTP caching behavior (?): OK
JavaScript-based tests (?): OK
DNS Tests –
Restricted domain DNS lookup (?): OK
We can successfully look up a name which resolves to the same IP address as our webserver. This means we are able to conduct many of the tests on your DNS server.
Unrestricted domain DNS lookup (?): OK
We can successfully look up arbitrary names from within the Java applet. This means we are able to conduct all test on your DNS server.
Direct DNS support (?): OK
All tested DNS types were received OK.
Direct EDNS support (?): OK
EDNS-enabled requests for small responses are answered successfully.
EDNS-enabled requests for medium-sized responses are answered successfully.
EDNS-enabled requests for large responses are answered successfully.
DNS resolver address (?): OK
The IP address of your ISP's DNS Resolver is 74.125.126.90, which does not resolve. Additional nameservers observed for your host: 74.125.126.85, 74.125.126.94, 74.125.126.82.
DNS resolver properties (?): Lookup latency 969ms
Your ISP's DNS resolver requires 969 msec to conduct an external lookup. It takes 37 msec for your ISP's DNS resolver to lookup a name on our server. 
This is particularly slow, and you may see significant performance degradation as a result.
Your resolver correctly uses TCP requests when necessary.
Your resolver is using QTYPE=A for default queries.
Your resolver is not automatically performing IPv6 queries.
Your DNS resolver does not use EDNS.
Your DNS resolver accepts DNS responses of up to 512 bytes.
Your resolver uses 0x20 randomization.
Your ISP's DNS server cannot use IPv6.
No transport problems were discovered which could affect the deployment of DNSSEC.
Direct probing of DNS resolvers (?)
Your system is configured to use 2 DNS resolver(s).
The resolver at 8.8.8.8 could not process the following tested types:
Large (~3000B) TXT records fetched with EDNS0
It does not validate DNSSEC. It does not wildcard NXDOMAIN errors.
The resolver at 8.8.4.4 can process all tested types. It does not validate DNSSEC. It does not wildcard NXDOMAIN errors.
DNS glue policy (?): OK
Your ISP's DNS resolver does not accept generic additional (glue) records — good.
Your ISP's DNS resolver does not accept additional (glue) records which correspond to nameservers.
Your ISP's DNS resolver follows CNAMEs when it is in a subdomain of the queried domain.
DNS resolver port randomization (?): OK
Your ISP's DNS resolver properly randomizes its local port number.
The following graph shows DNS requests on the x-axis and the detected source ports on the y-axis.

DNS lookups of popular domains (?): OK
24 of 90 popular names were resolved successfully. The most likely cause for failed forward lookups is a transient network issue. Show all names.
3 popular names have a mild anomaly. The ownership suggested by the reverse name lookup does not match our understanding of the original name. The most likely cause is the site's use of a Content Delivery Network. Show all names.
DNS external proxy (?): OK
Your host ignores external DNS requests.
DNS results wildcarding (?): OK
Your ISP correctly leaves non-resolving names untouched.
DNS-level redirection of specific sites (?): OK
Your ISP does not appear to be using DNS to redirect traffic for specific websites.
Direct probing of DNS roots (?)
We checked which DNS root server instances your computer can reach. 12 of 13 root servers responded. Show them.
IPv6 Tests +
DNS support for IPv6 (?): OK
IPv4, IPv6, and your web browser (?): IPv6 connectivity problem
IPv6 connectivity (?): No IPv6 support
Host Properties +
System clock accuracy (?): OK
Browser properties (?): OK
Uploaded data (?): OK


---

### Post by jcd29 on 2012-01-13
I'm close to giving up. So weird, this problem.

---

### Post by spacecheck on 2012-01-14
> **jcd29 said:**
> I'm close to giving up. So weird, this problem.
  Patience is a virtue, perseverance a strength.
Your earlier netalyzr exam showed the following:

> The IP address of your ISP's DNS Resolver is 74.125.126.90, which does  not resolve. Additional nameservers observed for your host:  74.125.126.85, 74.125.126.94, 74.125.126.82.
DNS resolver properties (?): Lookup latency 969ms
Your ISP's DNS resolver requires 969 msec to conduct an external lookup.  It takes 37 msec for your ISP's DNS resolver to lookup a name on our  server. 
This is particularly slow, and you may see significant performance degradation as a result.
What is listed in your /etc/resolve.conf file ?

Good luck!

---

### Post by jcd29 on 2012-01-14
> **spacecheck said:**
> Patience is a virtue, perseverance a strength.
Your earlier netalyzr exam showed the following:


What is listed in your /etc/resolve.conf file ?

Good luck!

```
cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 8.8.8.8
nameserver 8.8.4.4

```

---

### Post by spacecheck on 2012-01-14
What DNS server is entered into the router?
What happens, for example, as a test, if you enter your router address into the resolv.conf file, instead of the cited nameservers, then set the cited DNS servers, or alternatives, into the router, instead of those from the ISP, then restart the network and try to reach something?

My resolv.conf shows only the router. When a request hits the router, it resolves the address instead of the system having to do it. This happens on a LiveCD as well, since you automatically (DHCP) get access without having to enter DNS data after booting the LiveCd.

Also, have you ever used a proxy? Might there be a proxy set in Ubuntu for a different location, which now gets in the way, but was never set in the Windows system, thus only causes a problem in Ubuntu?

Happy hunting!

---

### Post by jcd29 on 2012-01-15
> **spacecheck said:**
> What DNS server is entered into the router?
What happens, for example, as a test, if you enter your router address into the resolv.conf file, instead of the cited nameservers, then set the cited DNS servers, or alternatives, into the router, instead of those from the ISP, then restart the network and try to reach something?

My resolv.conf shows only the router. When a request hits the router, it resolves the address instead of the system having to do it. This happens on a LiveCD as well, since you automatically (DHCP) get access without having to enter DNS data after booting the LiveCd.

Also, have you ever used a proxy? Might there be a proxy set in Ubuntu for a different location, which now gets in the way, but was never set in the Windows system, thus only causes a problem in Ubuntu?

Happy hunting!

Tried this but still the same :(

Also, I ran netalyzr in Ubuntu 11.04 live cd and it was still slow so I was mistaken.

However, I ran it in Fedora Live CD and Ubuntu 11.10 live CD and everything turned out just fine. Weird.

---

### Post by spacecheck on 2012-01-16
> I've had Ubuntu 11.04 for quite a few months now and my browsing speed has been just fine You mentioned in post#6
> Also, I ran netalyzr in Ubuntu 11.04 live cd and it was still slow so I was mistaken.

However, I ran it in Fedora Live CD and Ubuntu 11.10 live CD and everything turned out just fine. Weird.I initially though it might perhaps be system related, but it could also easily be due to short traffic spikes at the ISP or at the ISP's connection to the backbone, or farther up the line. Short enough to temporarily resolve (for example during a reboot into other OS or LiveCd), but return to annoy.

NetalyZr did point to a problem with the response time of the ISP. Have you tried [http://speedtest.net/](http://speedtest.net/) or other access tests besides netalyZr?

Are any of the really slow sites responding more immediately, if you browse their IP address as URL instead of using their domain names? With speedtest, you can select diverse test locations, which might give some indication of a directional problem.

BTW, I was glancing back over some past problems and found something which may be of interest:
[http://ubuntuforums.org/showpost.php?p=11598119&postcount=16](http://ubuntuforums.org/showpost.php?p=11598119&postcount=16)

Might be worth a look.

Good luck!

---

### Post by jcd29 on 2012-01-18
> **spacecheck said:**
> You mentioned in post#6
I initially though it might perhaps be system related, but it could also easily be due to short traffic spikes at the ISP or at the ISP's connection to the backbone, or farther up the line. Short enough to temporarily resolve (for example during a reboot into other OS or LiveCd), but return to annoy.

NetalyZr did point to a problem with the response time of the ISP. Have you tried [http://speedtest.net/](http://speedtest.net/) or other access tests besides netalyZr?

Are any of the really slow sites responding more immediately, if you browse their IP address as URL instead of using their domain names? With speedtest, you can select diverse test locations, which might give some indication of a directional problem.

BTW, I was glancing back over some past problems and found something which may be of interest:
[http://ubuntuforums.org/showpost.php?p=11598119&postcount=16](http://ubuntuforums.org/showpost.php?p=11598119&postcount=16)

Might be worth a look.

Good luck!
I formatted and installed 11.10 before reading this, but I think that was exactly it since I had recently put "wins" there. Thanks!

---

