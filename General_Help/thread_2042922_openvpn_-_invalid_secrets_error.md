---
title: "openvpn - invalid secrets error"
date: 2012-08-15
forum: General Help
---

### Post by qwertyjjj on 2012-08-15
I copied my certs and keys to /etc/openvpn.
I setup the network manager but when I connect it say failed due to invalid secrets error.
I imported settings from the .ovpn file and certs are definitely valid.
Any ideas, why?

---

### Post by qwertyjjj on 2012-08-16
from syslog:
```

Aug 16 08:14:01 usb-Inspiron-9300 NetworkManager[1233]: <info> Starting VPN service 'openvpn'...
Aug 16 08:14:05 usb-Inspiron-9300 NetworkManager[1233]: <info> VPN service 'openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 2617
Aug 16 08:14:05 usb-Inspiron-9300 NetworkManager[1233]: <info> VPN service 'openvpn' appeared; activating connections
Aug 16 08:14:07 usb-Inspiron-9300 NetworkManager[1233]: <info> VPN plugin state changed: starting (3)
Aug 16 08:14:07 usb-Inspiron-9300 NetworkManager[1233]: <info> VPN connection 'clientFR' (Connect) reply received.
Aug 16 08:14:07 usb-Inspiron-9300 nm-openvpn[2622]: OpenVPN 2.2.1 i686-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Mar 30 2012
Aug 16 08:14:07 usb-Inspiron-9300 nm-openvpn[2622]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Aug 16 08:14:07 usb-Inspiron-9300 nm-openvpn[2622]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Aug 16 08:14:07 usb-Inspiron-9300 nm-openvpn[2622]: LZO compression initialized
Aug 16 08:14:07 usb-Inspiron-9300 nm-openvpn[2622]: UDPv4 link local: [undef]
Aug 16 08:14:07 usb-Inspiron-9300 nm-openvpn[2622]: UDPv4 link remote: [AF_INET]84.xxx.xxx.xx:1194
Aug 16 08:14:08 usb-Inspiron-9300 nm-openvpn[2622]: WARNING: 'link-mtu' is used inconsistently, local='link-mtu 1542', remote='link-mtu 1546'
Aug 16 08:14:08 usb-Inspiron-9300 nm-openvpn[2622]: WARNING: 'mtu-dynamic' is present in remote config but missing in local config, remote='mtu-dynamic'
Aug 16 08:14:08 usb-Inspiron-9300 nm-openvpn[2622]: [ProxyPlayer.eu] Peer Connection Initiated with [AF_INET]84.xxx.xxx.xx:1194
Aug 16 08:14:10 usb-Inspiron-9300 nm-openvpn[2622]: AUTH: Received AUTH_FAILED control message
Aug 16 08:14:10 usb-Inspiron-9300 nm-openvpn[2622]: SIGTERM[soft,auth-failure] received, process exiting
Aug 16 08:14:10 usb-Inspiron-9300 NetworkManager[1233]: <warn> VPN plugin failed: 0
Aug 16 08:14:10 usb-Inspiron-9300 NetworkManager[1233]: <info> VPN plugin state changed: stopped (6)
Aug 16 08:14:10 usb-Inspiron-9300 NetworkManager[1233]: <info> VPN plugin state change reason: 10
Aug 16 08:14:10 usb-Inspiron-9300 NetworkManager[1233]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Aug 16 08:14:10 usb-Inspiron-9300 NetworkManager[1233]: <info> Policy set 'virginmedia7554601 1' (wlan0) as default for IPv4 routing and DNS.
Aug 16 08:14:15 usb-Inspiron-9300 NetworkManager[1233]: <info> VPN service 'openvpn' disappeared

```

[[IMG]http://img641.imageshack.us/img641/4492/screenshotfrom201208160.png[/IMG]](http://imageshack.us/photo/my-images/641/screenshotfrom201208160.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

