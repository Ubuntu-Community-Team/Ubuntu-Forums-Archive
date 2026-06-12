---
title: "OpenVPN problem - unable to connect"
date: 2009-12-16
forum: General Help
---

### Post by OobNosferatu on 2009-12-16
I've been using an UltraVPN account and had it set up using the gnome network manager. It was working just fine for the last couple of months, when all of a sudden it doesn't connect anymore. FYI: I do have network-manager-openvpn installed. It was working earlier...

Here's my syslog:

```

Dec 16 10:35:52 My-laptop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'... 
Dec 16 10:35:52 My-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 13200 
Dec 16 10:35:52 My-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections 
Dec 16 10:35:55 My-laptop NetworkManager: <info>  VPN plugin state changed: 3 
Dec 16 10:35:55 My-laptop NetworkManager: <info>  VPN connection 'VPN connection 1' (Connect) reply received. 
Dec 16 10:35:55 My-laptop nm-openvpn[13212]: OpenVPN 2.1_rc11 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Mar  9 2009
Dec 16 10:35:55 My-laptop nm-openvpn[13212]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Dec 16 10:35:55 My-laptop nm-openvpn[13212]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Dec 16 10:35:55 My-laptop nm-openvpn[13212]: LZO compression initialized
Dec 16 10:35:55 My-laptop nm-openvpn[13212]: UDPv4 link local: [undef]
Dec 16 10:35:55 My-laptop nm-openvpn[13212]: UDPv4 link remote: 87.98.173.225:443
Dec 16 10:35:55 My-laptop nm-openvpn[13212]: WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Dec 16 10:35:56 My-laptop nm-openvpn[13212]: [ludwig] Peer Connection Initiated with 87.98.173.225:443
Dec 16 10:35:57 My-laptop nm-openvpn[13212]: OpenVPN ROUTE: OpenVPN needs a gateway parameter for a --route option and no default was specified by either --route-gateway or --ifconfig options
Dec 16 10:35:57 My-laptop nm-openvpn[13212]: OpenVPN ROUTE: failed to parse/resolve route for host/network: 10.8.0.1
Dec 16 10:35:57 My-laptop nm-openvpn[13212]: TUN/TAP device tun0 opened
Dec 16 10:35:57 My-laptop nm-openvpn[13212]: /usr/lib/network-manager-openvpn/nm-openvpn-service-openvpn-helper tun0 1500 1542   init
Dec 16 10:35:57 My-laptop kernel: [10192.946183] tun0: Disabled Privacy Extensions
Dec 16 10:35:57 My-laptop NetworkManager: <info>  VPN plugin failed: 2 
Dec 16 10:35:57 My-laptop nm-openvpn[13212]: script failed: external program exited with error status: 1
Dec 16 10:35:57 My-laptop nm-openvpn[13212]: Exiting
Dec 16 10:35:57 My-laptop NetworkManager: <info>  VPN plugin failed: 1 
Dec 16 10:35:57 My-laptop NetworkManager: <info>  VPN plugin state changed: 6 
Dec 16 10:35:57 My-laptop NetworkManager: <info>  VPN plugin state change reason: 0 
Dec 16 10:35:57 My-laptop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Dec 16 10:35:57 My-laptop NetworkManager: <info>  Policy set 'Auto HISD' (wlan0) as default for routing and DNS. 
Dec 16 10:36:10 My-laptop NetworkManager: <debug> [1260981370.001286] ensure_killed(): waiting for vpn service pid 13200 to exit 
Dec 16 10:36:10 My-laptop NetworkManager: <debug> [1260981370.001453] ensure_killed(): vpn service pid 13200 cleaned up 

```

I googled the following error from the syslog, but to no avail:

```
OpenVPN ROUTE: failed to parse/resolve route for host/network:
```

Most of the sites that showed up were in a different language and the ones I translated didn't help.

Could someone please point me in the right direction? What other information or insight do I need to figure out the problem?

PS: I must add that I'm able to connect just fine using the command line, using "sudo /etc/init.d/openvpn start"

---

