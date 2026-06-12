---
title: "PPTP VPN not working"
date: 2009-11-21
forum: General Help
---

### Post by pmains on 2009-11-21
I've enabled, PAP, CHAP, MSCHAP and MSCHAPv2. I enabled "Use Point-to-Point encryption (MPPE)." However, I just can't seem to get rid of the following error when I connect to VPN.

```
Nov 21 15:35:02 providence NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Nov 21 15:35:02 providence NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 5240
Nov 21 15:35:02 providence NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Nov 21 15:35:02 providence NetworkManager: <info>  VPN plugin state changed: 3
Nov 21 15:35:02 providence NetworkManager: <info>  VPN connection '[ connection name ]' (Connect) reply received.
Nov 21 15:35:02 providence NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov 21 15:35:02 providence NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Nov 21 15:35:02 providence pptp[5245]: nm-pptp-service-5240 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Nov 21 15:35:02 providence pptp[5251]: nm-pptp-service-5240 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Nov 21 15:35:02 providence pptp[5251]: nm-pptp-service-5240 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Nov 21 15:35:02 providence pptp[5251]: nm-pptp-service-5240 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Nov 21 15:35:03 providence pptp[5251]: nm-pptp-service-5240 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Nov 21 15:35:03 providence pptp[5251]: nm-pptp-service-5240 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Nov 21 15:35:03 providence pptp[5251]: nm-pptp-service-5240 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 5757).
Nov 21 15:35:03 providence pptp[5251]: nm-pptp-service-5240 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Nov 21 15:35:03 providence pptp[5251]: nm-pptp-service-5240 log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
Nov 21 15:35:03 providence pptp[5251]: nm-pptp-service-5240 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Nov 21 15:35:03 providence pptp[5251]: nm-pptp-service-5240 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Nov 21 15:35:03 providence pptp[5251]: nm-pptp-service-5240 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Nov 21 15:35:03 providence NetworkManager: <info>  VPN plugin failed: 1
Nov 21 15:35:03 providence NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov 21 15:35:03 providence NetworkManager: <info>  VPN plugin failed: 1
Nov 21 15:35:03 providence NetworkManager: <info>  VPN plugin state changed: 6
Nov 21 15:35:03 providence NetworkManager: <info>  VPN plugin state change reason: 0
Nov 21 15:35:03 providence NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Nov 21 15:35:03 providence NetworkManager: <info>  (wlan0): writing resolv.conf to /sbin/resolvconf
Nov 21 15:35:03 providence NetworkManager: <info>  Policy set 'Auto []' (wlan0) as default for routing and DNS.
```

Any ideas?

---

### Post by twotwenty on 2009-12-17
Im also in the same boat, Im using 9.10 karmic, I have all the same th ings enabled, Im also using dd0wrt v24 with chap name and password

---

