---
title: "How to install OpenVPN"
date: 2012-09-29
forum: General Help
---

### Post by Mycotheologist on 2012-09-29
I want to learn how to access the internet through a VPN and I hear OpenVPN is a good free VPN. So I started following this tutorial:
[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)
but I can't even get past the first step. They instruct you to edit **/etc/network/interfaces** and they say this file should look something like this:
> # This file describes the network interfaces available on your system # and how to activate them. For more information, see interfaces(5).  # The loopback network interface auto lo eth0 iface lo inet loopback  # The primary network interface ## This device provides internet access. iface eth0 inet static   address 192.168.1.10   netmask 255.255.255.0   gateway 192.168.1.1

but when I opened up the interfaces file on my laptop, heres whats in it:
> auto lo
iface lo inet loopback

What am I missing here?

---

