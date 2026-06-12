---
title: "OpenVPN certificate issue"
date: 2011-05-29
forum: General Help
---

### Post by Webgirl on 2011-05-29
I'm using Ubuntu 10.04 LTS and trying to set up OpenVPN according to the [ubuntu tutorial]("https://help.ubuntu.com/10.10/serverguide/C/openvpn.html"). I had some problems setting up the bridge, but finally got it running without errors. 

So I continued the tutorial and installed OpenVPN. However I'm having some issues setting up the certificates. I navigated to /etc/openvpn/easy-rsa but when I enter 
```
source vars
```

nothing happens. When I go to the next line

```
./clean-all
```

I get an error message stating 

```
bash: ./clean-all: No such file or directory
```

Clearly, something somewhere didn't get set up correctly or didn't initalize the way it's supposed to. But I'm not sure where. The bridge is up and running, here's the /etc/network/interfaces file.
```
auto lo
iface lo inet loopback

#bridge between eth0 and eth1
auto br0

iface br0 inet static
address 192.168.1.3
netmask 255.255.248.0
network 192.168.1.0
broadcast 192.168.1.1
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off
```

How do I get these certificates working?

---

