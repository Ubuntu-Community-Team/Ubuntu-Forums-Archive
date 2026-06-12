---
title: "Internet not working"
date: 2010-01-31
forum: General Help
---

### Post by avee137 on 2010-01-31
Hi,
M new to ubuntu.m usin ubuntu9.10. In beginnin Internet was workin fine with auto eth0 establishing connection automatically.Once i got some notification regarding some ' serious kernel failure'.And wen i rebooted the system,internet was gone.However internet is runnin fine on win7,which is installed on a separate partition on hard disk.Is there any way out other than re-installation??

Thanks.

---

### Post by t4thfavor on 2010-01-31
If it doesn't come back after a reboot, you should check the config in networkmanager, there have been a bunch of bugs in that program as of late.

---

### Post by blueshiftoverwatch on 2010-01-31
You could always try giving your computer a static IP address instead of using DHCP, which is what's configured by default.

Just amend */etc/network/interfaces* with whatever your information is:
```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address xxx.xxx.xxx.xxx
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx
```
If your not sure what your netmark or gateway addresses are, just run **ifconfig** in the terminal and it should tell you. Gateway is the address of your router and netmask is generally 255.255.255.0.

Also, make sure that your static IP address isn't in the same range as your router's DHCP assigned IP addresses. Or another computer could connect to your network using DHCP and have it conflict with your static IP address. On my Linksys router the default DHCP addresses were something like 192.168.1.100 through 192.186.1.140. To check, just type in your public IP address into your browser's address bar. Try the password "admin" with no username if your router is a Linksys. If it's not, a web search for "default password for <insert_router_name> should bring up answers.

---

