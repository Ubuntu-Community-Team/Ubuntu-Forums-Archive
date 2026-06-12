---
title: "problem with ifup and ifdown"
date: 2010-05-17
forum: General Help
---

### Post by zyothi on 2010-05-17
Hi,

I am facing problem with ifup and ifdown. I am using wired connection whose ip is manually set. I am using Ubuntu 9.10 karmic

I have these entries in the /etc/network/interfaces file

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.6.26.25
netmask 255.255.0.0
gateway 10.6.0.254
broadcast 10.6.255.255

In order to use ifup/down I need these entries to be there in  /etc/network/interfaces file. But when I restart the machine my network is down showing **device not managed**. It is not showing any connection though it is connected. This might be the old problem but with the existing solution I could not resolve this. Please tell me what might be wrong with it.

Thanks

---

