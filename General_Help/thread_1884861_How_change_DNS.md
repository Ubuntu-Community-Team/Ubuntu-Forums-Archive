---
title: "How change DNS"
date: 2011-11-22
forum: General Help
---

### Post by xavi fernandez on 2011-11-22
Hi, I'm trying install the vpn but everything fails until now, I contact with the company and they told me I need change the DNS for this 80.67.0.2

I try find some how to, I'm really new in linux and I didn't find anything. Please, can some one help me with this in a easy way to understand? Will be much appreciate.

Thanks in advance

---

### Post by xavi fernandez on 2011-11-22
thanks for your fast reply bkerensa, I'm running ubuntu 11.10

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric

Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

This is what I found, it is enough?

---

### Post by effenberg0x0 on 2011-11-22
> **xavi fernandez said:**
> Hi, I'm trying install the vpn but everything fails until now, I contact with the company and they told me I need change the DNS for this 80.67.0.2

I try find some how to, I'm really new in linux and I didn't find anything. Please, can some one help me with this in a easy way to understand? Will be much appreciate.

Thanks in advance

DNS entries in default Ubuntu are placed in /etc/resolv.conf. So, basically, if you sudo gedit /etc/resolv.conf and enter the desired DNs there, they immediately start being used. See my /etc/resolv.conf below:

```
[07:51 AM][ahsl:AL-DESK:~/.config/dconf]
$ cat /etc/resolv.conf
#Local DNS
nameserver 192.168.1.3
# Google 1st and 2nd
nameserver 8.8.8.8
nameserver 4.4.4.4
# OpenDNS 1st and 2nd
nameserver 208.67.222.222
nameserver 208.67.220.220
```The thing is: I don't use network-manager - I use fixed IPs, DNS, etc in my network. If you are on a PC that uses network-manager to get an IP and network settings (DNS, etc) from a DHCP server (which is very likely), your changes to resolv.conf will be lost when you reboot. 

Why is it like that? Suppose you're on a laptop, roaming between wireless access points. As you change between different routers, you will receive new dhcp connection offers from them and, as you connect to them, you'll receive a different IP and DNS settings so you can probably use the connections. Network-manager handles that automatically.

If you still want to add custom DNS servers, even if you are using network-manager, please read item B of the FAQ by the end of the following wiki page:
[https://help.ubuntu.com/community/NetworkManager0.7#FAQ.2BAC8-Common_issues.2BAC8-Pitfalls](https://help.ubuntu.com/community/NetworkManager0.7#FAQ.2BAC8-Common_issues.2BAC8-Pitfalls)

---

### Post by polki@mac.com on 2011-11-23
Please use "gksu" instead of "sudo" for graphical applications.

"gksu gedit /etc/resolv.conf"

---

