---
title: "PPTP VPN Server Issues"
date: 2010-11-13
forum: General Help
---

### Post by JesseMoore on 2010-11-13
I am trying to connect to my Ubuntu Enterprise Cloud 10.04  PPTP VPN server from my school/work network.  I use the built-in VPN client in Windows 7 to do this, but I always get error 619.  If you could let me know possible ways to solve this, I would greatly appreciate it.  This is what /etc/log/syslog says:

Nov 13 13:53:24 web-vpn-server pptpd[4707]: MGR: Launching /usr/sbin/pptpctrl to handle client
Nov 13 13:53:24 web-vpn-server pptpd[4707]: CTRL: local address = 192.168.2.5
Nov 13 13:53:24 web-vpn-server pptpd[4707]: CTRL: remote address = 192.168.2.234
Nov 13 13:53:24 web-vpn-server pptpd[4707]: CTRL: pppd options file = /etc/ppp/pptpd-options
Nov 13 13:53:24 web-vpn-server pptpd[4707]: CTRL: Client 136.165.118.43 control connection started
Nov 13 13:53:24 web-vpn-server pptpd[4707]: CTRL: Received PPTP Control Message (type: 1)
Nov 13 13:53:24 web-vpn-server pptpd[4707]: CTRL: Made a START CTRL CONN RPLY packet
Nov 13 13:53:24 web-vpn-server pptpd[4707]: CTRL: I wrote 156 bytes to the client.
Nov 13 13:53:24 web-vpn-server pptpd[4707]: CTRL: Sent packet to client
Nov 13 13:53:24 web-vpn-server pptpd[4707]: CTRL: Received PPTP Control Message (type: 7)
Nov 13 13:53:24 web-vpn-server pptpd[4707]: CTRL: Set parameters to 100000000 maxbps, 64 window size
Nov 13 13:53:24 web-vpn-server pptpd[4707]: CTRL: Made a OUT CALL RPLY packet
Nov 13 13:53:24 web-vpn-server pptpd[4707]: CTRL: Starting call (launching pppd, opening GRE)
Nov 13 13:53:24 web-vpn-server pptpd[4707]: CTRL: pty_fd = 6
Nov 13 13:53:24 web-vpn-server pptpd[4707]: CTRL: tty_fd = 7
Nov 13 13:53:24 web-vpn-server pptpd[4707]: CTRL: I wrote 32 bytes to the client.
Nov 13 13:53:24 web-vpn-server pptpd[4707]: CTRL: Sent packet to client
Nov 13 13:53:24 web-vpn-server pptpd[4709]: CTRL (PPPD Launcher): program binary = /usr/sbin/pppd
Nov 13 13:53:24 web-vpn-server pptpd[4709]: CTRL (PPPD Launcher): local address = 192.168.2.5
Nov 13 13:53:24 web-vpn-server pptpd[4709]: CTRL (PPPD Launcher): remote address = 192.168.2.234
Nov 13 13:53:24 web-vpn-server pppd[4709]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Nov 13 13:53:24 web-vpn-server pppd[4709]: pptpd-logwtmp: $Version$
Nov 13 13:53:24 web-vpn-server pppd[4709]: pppd 2.4.5 started by root, uid 0
Nov 13 13:53:24 web-vpn-server pppd[4709]: using channel 3
Nov 13 13:53:24 web-vpn-server pppd[4709]: Using interface ppp0
Nov 13 13:53:24 web-vpn-server pppd[4709]: Connect: ppp0 <--> /dev/pts/0
Nov 13 13:53:24 web-vpn-server pppd[4709]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xabebafd5> <pcomp> <accomp>]
Nov 13 13:53:24 web-vpn-server pptpd[4707]: GRE: Bad checksum from pppd.
Nov 13 13:53:24 web-vpn-server pptpd[4707]: CTRL: Received PPTP Control Message (type: 15)
Nov 13 13:53:24 web-vpn-server pptpd[4707]: CTRL: Got a SET LINK INFO packet with standard ACCMs
Nov 13 13:53:24 web-vpn-server pptpd[4707]: GRE: accepting packet #0
Nov 13 13:53:24 web-vpn-server pppd[4709]: rcvd [LCP ConfReq id=0x0 <mru 1400> <magic 0xb02396b> <pcomp> <accomp> <callback CBCP>]
Nov 13 13:53:24 web-vpn-server pppd[4709]: sent [LCP ConfRej id=0x0 <callback CBCP>]
Nov 13 13:53:26 web-vpn-server pptpd[4707]: GRE: accepting packet #1
Nov 13 13:53:26 web-vpn-server pppd[4709]: rcvd [LCP ConfReq id=0x1 <mru 1400> <magic 0xb02396b> <pcomp> <accomp> <callback CBCP>]
Nov 13 13:53:26 web-vpn-server pppd[4709]: sent [LCP ConfRej id=0x1 <callback CBCP>]
Nov 13 13:53:27 web-vpn-server pppd[4709]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xabebafd5> <pcomp> <accomp>]

Nov 13 13:53:29 web-vpn-server pptpd[4707]: GRE: accepting packet #2
Nov 13 13:53:29 web-vpn-server pppd[4709]: rcvd [LCP ConfReq id=0x2 <mru 1400> <magic 0xb02396b> <pcomp> <accomp> <callback CBCP>]
Nov 13 13:53:29 web-vpn-server pppd[4709]: sent [LCP ConfRej id=0x2 <callback CBCP>]
Nov 13 13:53:30 web-vpn-server pppd[4709]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xabebafd5> <pcomp> <accomp>]
Nov 13 13:53:33 web-vpn-server pppd[4709]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xabebafd5> <pcomp> <accomp>]
Nov 13 13:53:33 web-vpn-server pptpd[4707]: GRE: accepting packet #3
Nov 13 13:53:33 web-vpn-server pppd[4709]: rcvd [LCP ConfReq id=0x3 <mru 1400> <magic 0xb02396b> <pcomp> <accomp> <callback CBCP>]
Nov 13 13:53:33 web-vpn-server pppd[4709]: sent [LCP ConfRej id=0x3 <callback CBCP>]
Nov 13 13:53:36 web-vpn-server pppd[4709]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xabebafd5> <pcomp> <accomp>]
Nov 13 13:53:37 web-vpn-server pptpd[4707]: GRE: accepting packet #4
Nov 13 13:53:37 web-vpn-server pppd[4709]: rcvd [LCP ConfReq id=0x4 <mru 1400> <magic 0xb02396b> <pcomp> <accomp> <callback CBCP>]
Nov 13 13:53:37 web-vpn-server pppd[4709]: sent [LCP ConfRej id=0x4 <callback CBCP>]
Nov 13 13:53:39 web-vpn-server pppd[4709]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xabebafd5> <pcomp> <accomp>]
Nov 13 13:53:41 web-vpn-server pptpd[4707]: GRE: accepting packet #5
Nov 13 13:53:41 web-vpn-server pppd[4709]: rcvd [LCP ConfReq id=0x5 <mru 1400> <magic 0xb02396b> <pcomp> <accomp> <callback CBCP>]
Nov 13 13:53:41 web-vpn-server pppd[4709]: sent [LCP ConfRej id=0x5 <callback CBCP>]
Nov 13 13:53:42 web-vpn-server pppd[4709]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xabebafd5> <pcomp> <accomp>]
Nov 13 13:53:45 web-vpn-server pppd[4709]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xabebafd5> <pcomp> <accomp>]
Nov 13 13:53:46 web-vpn-server pptpd[4707]: GRE: accepting packet #6
Nov 13 13:53:46 web-vpn-server pppd[4709]: rcvd [LCP ConfReq id=0x6 <mru 1400> <magic 0xb02396b> <pcomp> <accomp> <callback CBCP>]
Nov 13 13:53:46 web-vpn-server pppd[4709]: sent [LCP ConfRej id=0x6 <callback CBCP>]
Nov 13 13:53:48 web-vpn-server pppd[4709]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xabebafd5> <pcomp> <accomp>]
Nov 13 13:53:50 web-vpn-server pptpd[4707]: GRE: accepting packet #7
Nov 13 13:53:50 web-vpn-server pppd[4709]: rcvd [LCP ConfReq id=0x7 <mru 1400> <magic 0xb02396b> <pcomp> <accomp> <callback CBCP>]
Nov 13 13:53:50 web-vpn-server pppd[4709]: sent [LCP ConfRej id=0x7 <callback CBCP>]
Nov 13 13:53:51 web-vpn-server pppd[4709]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xabebafd5> <pcomp> <accomp>]
Nov 13 13:53:54 web-vpn-server pptpd[4707]: GRE: accepting packet #8
Nov 13 13:53:54 web-vpn-server pppd[4709]: rcvd [LCP ConfReq id=0x8 <mru 1400> <magic 0xb02396b> <pcomp> <accomp> <callback CBCP>]
Nov 13 13:53:54 web-vpn-server pppd[4709]: sent [LCP ConfRej id=0x8 <callback CBCP>]
Nov 13 13:53:54 web-vpn-server pppd[4709]: LCP: timeout sending Config-Requests
Nov 13 13:53:54 web-vpn-server pppd[4709]: Connection terminated.
Nov 13 13:53:54 web-vpn-server pppd[4709]: Modem hangup
Nov 13 13:53:54 web-vpn-server pppd[4709]: Exit.
Nov 13 13:53:54 web-vpn-server pptpd[4707]: GRE: read(fd=6,buffer=805a540,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused $
Nov 13 13:53:54 web-vpn-server pptpd[4707]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Nov 13 13:53:54 web-vpn-server pptpd[4707]: CTRL: Reaping child PPP[4709]
Nov 13 13:53:54 web-vpn-server pptpd[4707]: CTRL: Client 136.165.118.43 control connection finished
Nov 13 13:53:54 web-vpn-server pptpd[4707]: CTRL: Exiting now
Nov 13 13:53:54 web-vpn-server pptpd[1133]: MGR: Reaped child 4707

---

