---
title: "VPN (Relakks) connection timeout every time [help me analyze syslog]"
date: 2010-06-21
forum: General Help
---

### Post by revered on 2010-06-21
I have been trying to use relakks on ubuntu 10.04 using the network manager. First it just said "failed" but now after changing some settings I am getting timeout everytime. These are the settings:

gateway: pptp.relakks.com
authentification: MSCHAP & MSCHAPv2 checked (everything else unchecked)
use point to point encryption: checked - 128 bit
allow bsd data compression: checked
allow deflate data compression: checked
use tcp header compression: checked

And here's the syslog

```
Jun 21 16:38:03 desktop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Jun 21 16:38:03 desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 1642
Jun 21 16:38:03 desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Jun 21 16:38:03 desktop NetworkManager: <info>  VPN plugin state changed: 1
Jun 21 16:38:03 desktop NetworkManager: <info>  VPN plugin state changed: 3
Jun 21 16:38:03 desktop NetworkManager: <info>  VPN connection 'Relakks' (Connect) reply received.
Jun 21 16:38:03 desktop pppd[1645]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Jun 21 16:38:03 desktop pppd[1645]: pppd 2.4.5 started by root, uid 0
Jun 21 16:38:03 desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Jun 21 16:38:03 desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp1, iface: ppp1): no ifupdown configuration found.
Jun 21 16:38:03 desktop pppd[1645]: Using interface ppp1
Jun 21 16:38:03 desktop pppd[1645]: Connect: ppp1 <--> /dev/pts/0
Jun 21 16:38:05 desktop pptp[1649]: nm-pptp-service-1642 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jun 21 16:38:09 desktop pptp[1658]: nm-pptp-service-1642 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jun 21 16:38:10 desktop pptp[1658]: nm-pptp-service-1642 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jun 21 16:38:10 desktop pptp[1658]: nm-pptp-service-1642 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jun 21 16:38:10 desktop pptp[1658]: nm-pptp-service-1642 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jun 21 16:38:11 desktop pptp[1658]: nm-pptp-service-1642 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jun 21 16:38:11 desktop pptp[1658]: nm-pptp-service-1642 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 47360).
Jun 21 16:38:12 desktop pppd[1645]: CHAP authentication succeeded
Jun 21 16:38:12 desktop pppd[1645]: MPPE 128-bit stateless compression enabled
Jun 21 16:38:13 desktop pppd[1645]: Cannot determine ethernet address for proxy ARP
Jun 21 16:38:13 desktop pppd[1645]: local  IP address 93.182.138.3
Jun 21 16:38:13 desktop pppd[1645]: remote IP address 93.182.138.2
Jun 21 16:38:13 desktop pppd[1645]: primary   DNS address 93.182.182.85
Jun 21 16:38:13 desktop pppd[1645]: secondary DNS address 93.182.182.85
Jun 21 16:38:24 desktop pptp[1649]: nm-pptp-service-1642 log[decaps_gre:pptp_gre.c:414]: buffering packet 35 (expecting 34, lost or reordered)
Jun 21 16:38:36 desktop pptp[1649]: nm-pptp-service-1642 log[decaps_gre:pptp_gre.c:414]: buffering packet 61 (expecting 60, lost or reordered)
Jun 21 16:38:36 desktop pptp[1649]: nm-pptp-service-1642 log[decaps_gre:pptp_gre.c:414]: buffering packet 62 (expecting 60, lost or reordered)
Jun 21 16:38:36 desktop pptp[1649]: nm-pptp-service-1642 log[decaps_gre:pptp_gre.c:414]: buffering packet 63 (expecting 60, lost or reordered)
Jun 21 16:38:36 desktop pptp[1649]: nm-pptp-service-1642 log[decaps_gre:pptp_gre.c:414]: buffering packet 64 (expecting 60, lost or reordered)
Jun 21 16:38:36 desktop pptp[1649]: nm-pptp-service-1642 log[decaps_gre:pptp_gre.c:414]: buffering packet 65 (expecting 60, lost or reordered)
Jun 21 16:38:42 desktop pptp[1649]: nm-pptp-service-1642 log[decaps_gre:pptp_gre.c:414]: buffering packet 82 (expecting 81, lost or reordered)
Jun 21 16:38:42 desktop pptp[1649]: nm-pptp-service-1642 log[decaps_gre:pptp_gre.c:414]: buffering packet 83 (expecting 81, lost or reordered)
Jun 21 16:38:42 desktop pptp[1649]: nm-pptp-service-1642 log[decaps_gre:pptp_gre.c:414]: buffering packet 84 (expecting 81, lost or reordered)
Jun 21 16:38:42 desktop pptp[1649]: nm-pptp-service-1642 log[decaps_gre:pptp_gre.c:414]: buffering packet 85 (expecting 81, lost or reordered)
Jun 21 16:38:44 desktop NetworkManager: <info>  VPN connection 'Relakks' (IP Config Get) timeout exceeded.

**ALREADY FAILED, THE REST IS NOT VERY IMPORTANT** 

Jun 21 16:38:53 desktop pppd[1645]: Terminating on signal 15
Jun 21 16:38:53 desktop pppd[1645]: Connect time 0.7 minutes.
Jun 21 16:38:53 desktop pppd[1645]: Sent 0 bytes, received 4508 bytes.
Jun 21 16:38:53 desktop NetworkManager: <info>  Policy set 'Personal Default 1' (ppp0) as default for routing and DNS.
Jun 21 16:38:53 desktop pppd[1645]: MPPE disabled
Jun 21 16:38:53 desktop pppd[1645]: Child process /usr/sbin/pptp pptp.relakks.com --nolaunchpppd --logstring nm-pptp-service-1642 (pid 1647) terminated with signal 15
Jun 21 16:38:54 desktop pppd[1645]: Connection terminated.
Jun 21 16:38:54 desktop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Jun 21 16:38:54 desktop pppd[1645]: Exit.
Jun 21 16:38:54 desktop pptp[1649]: nm-pptp-service-1642 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Jun 21 16:38:54 desktop pptp[1649]: nm-pptp-service-1642 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Jun 21 16:38:54 desktop pptp[1658]: nm-pptp-service-1642 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Jun 21 16:38:54 desktop pptp[1658]: nm-pptp-service-1642 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jun 21 16:38:54 desktop pptp[1658]: nm-pptp-service-1642 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Jun 21 16:39:06 desktop NetworkManager: <debug> [1277149146.002113] ensure_killed(): waiting for vpn service pid 1642 to exit
Jun 21 16:39:06 desktop NetworkManager: <debug> [1277149146.002250] ensure_killed(): vpn service pid 1642 cleaned up
```

ppp0 is an usb mobile modem I use to connect to internet

Could anyone take a look to the syslog and give me some hints on why is timing out?

---

### Post by revered on 2010-06-24
Now it doesn't show timeout anymore, just failed

I have been researching about "no ifupdown configuration found" and "synchronous pptp option is NOT activated", tried a few tips but still can't get it working.

Does anyone see any known error or something in the syslog that can help me fix it?

The new syslog:

```
Jun 24 11:42:17 desktop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Jun 24 11:42:17 desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 3717
Jun 24 11:42:17 desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Jun 24 11:42:22 desktop NetworkManager: <info>  VPN plugin state changed: 3
Jun 24 11:42:22 desktop NetworkManager: <info>  VPN connection 'Relakks' (Connect) reply received.
Jun 24 11:42:22 desktop pppd[3720]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Jun 24 11:42:22 desktop pppd[3720]: pppd 2.4.5 started by root, uid 0
Jun 24 11:42:22 desktop pppd[3720]: Using interface ppp1
Jun 24 11:42:22 desktop pppd[3720]: Connect: ppp1 <--> /dev/pts/2
Jun 24 11:42:22 desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Jun 24 11:42:22 desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp1, iface: ppp1): no ifupdown configuration found.
Jun 24 11:42:24 desktop pptp[3724]: nm-pptp-service-3717 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jun 24 11:42:25 desktop pptp[3732]: nm-pptp-service-3717 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jun 24 11:42:26 desktop pptp[3732]: nm-pptp-service-3717 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jun 24 11:42:26 desktop pptp[3732]: nm-pptp-service-3717 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jun 24 11:42:26 desktop pptp[3732]: nm-pptp-service-3717 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jun 24 11:42:26 desktop kernel: [ 6367.004069] Inbound IN=ppp0 OUT= MAC= SRC=189.38.158.222 DST=186.110.36.32 LEN=132 TOS=0x00 PREC=0x00 TTL=114 ID=27835 PROTO=UDP SPT=35863 DPT=22015 LEN=112 
Jun 24 11:42:27 desktop pptp[3732]: nm-pptp-service-3717 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jun 24 11:42:27 desktop pptp[3732]: nm-pptp-service-3717 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 32256).
Jun 24 11:42:27 desktop kernel: [ 6367.324048] Inbound IN=ppp0 OUT= MAC= SRC=93.182.156.2 DST=186.110.36.32 LEN=61 TOS=0x00 PREC=0x00 TTL=52 ID=17830 DF PROTO=47 
Jun 24 11:42:27 desktop kernel: [ 6367.644059] Inbound IN=ppp0 OUT= MAC= SRC=93.182.156.2 DST=186.110.36.32 LEN=60 TOS=0x00 PREC=0x00 TTL=52 ID=17831 DF PROTO=47 
Jun 24 11:42:27 desktop kernel: [ 6367.664044] Inbound IN=ppp0 OUT= MAC= SRC=93.182.156.2 DST=186.110.36.32 LEN=60 TOS=0x00 PREC=0x00 TTL=52 ID=17832 DF PROTO=47 
Jun 24 11:42:27 desktop pptp[3732]: nm-pptp-service-3717 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Jun 24 11:42:27 desktop pptp[3732]: nm-pptp-service-3717 log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
Jun 24 11:42:27 desktop pptp[3732]: nm-pptp-service-3717 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jun 24 11:42:27 desktop pptp[3732]: nm-pptp-service-3717 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Jun 24 11:42:27 desktop pptp[3732]: nm-pptp-service-3717 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Jun 24 11:42:27 desktop pppd[3720]: Modem hangup
Jun 24 11:42:27 desktop pppd[3720]: Connection terminated.
Jun 24 11:42:27 desktop NetworkManager: <info>  VPN plugin failed: 1
Jun 24 11:42:27 desktop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Jun 24 11:42:27 desktop pppd[3720]: Exit.
Jun 24 11:42:27 desktop NetworkManager: <info>  VPN plugin failed: 1
Jun 24 11:42:27 desktop NetworkManager: <info>  VPN plugin failed: 1
Jun 24 11:42:27 desktop NetworkManager: <info>  VPN plugin state changed: 6
Jun 24 11:42:27 desktop NetworkManager: <info>  VPN plugin state change reason: 0
Jun 24 11:42:27 desktop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Jun 24 11:42:27 desktop NetworkManager: <info>  Policy set 'Personal Movil' (ppp0) as default for routing and DNS.
```

---

### Post by delwinv on 2010-11-10
I have this problem quite often, and recently almost all the time, even though under Windows it does work for me. It seems that for some reason Ubuntu is using the same bad ip address for pptp.relakks.com. I simply do an nslookup on pptp.relakks.com and choose one of the ip addresses to use, instead of typing pptp.relakks.com in the gateway box.
```
nslookup pptp.relakks.com
```
For me that resulted in:
```
Non-authoritative answer:
Name:	pptp.relakks.com
Address: 93.182.156.2
Name:	pptp.relakks.com
Address: 93.182.157.2
Name:	pptp.relakks.com
Address: 93.182.158.2
Name:	pptp.relakks.com
Address: 93.182.159.2
Name:	pptp.relakks.com
Address: 93.182.168.2
Name:	pptp.relakks.com
Address: 93.182.169.2
Name:	pptp.relakks.com
Address: 93.182.171.2
Name:	pptp.relakks.com
Address: 93.182.172.2
Name:	pptp.relakks.com
Address: 93.182.173.2
Name:	pptp.relakks.com
Address: 93.182.175.2
Name:	pptp.relakks.com
Address: 93.182.184.2
Name:	pptp.relakks.com
Address: 93.182.134.2
Name:	pptp.relakks.com
Address: 93.182.135.2
Name:	pptp.relakks.com
Address: 93.182.135.130
Name:	pptp.relakks.com
Address: 93.182.136.2
Name:	pptp.relakks.com
Address: 93.182.136.130
Name:	pptp.relakks.com
Address: 93.182.137.2
Name:	pptp.relakks.com
Address: 93.182.144.2
Name:	pptp.relakks.com
Address: 93.182.154.2
Name:	pptp.relakks.com
Address: 93.182.155.2

```

---

### Post by ds9 on 2011-03-18
> **delwinv said:**
> I have this problem quite often, and recently almost all the time, even though under Windows it does work for me. It seems that for some reason Ubuntu is using the same bad ip address for pptp.relakks.com. I simply do an nslookup on pptp.relakks.com and choose one of the ip addresses to use, instead of typing pptp.relakks.com in the gateway box...
.....


I face the same bug. 
It has been reported : [https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/681739](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/681739)
Let's mention we face the same issue.

---

