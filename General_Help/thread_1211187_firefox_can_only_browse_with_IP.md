---
title: "firefox can only browse with IP"
date: 2009-07-12
forum: General Help
---

### Post by ultimatebuster on 2009-07-12
Hi!
I just replaced Firefox 3.0 bundled with Ubuntu 9.04 with Firefox 3.5. All the sudden I cannot browse sites like google.com. However, I can browse google.com if I entered the IP address of the site.

What's going on?
Thanks in advanced.

---

### Post by sasho_zl on 2009-07-12
It seems to be a problem with the DNS. I can't figure out how a firefox replacement could affect this. Do you use a router?

---

### Post by ultimatebuster on 2009-07-12
> **sasho_zl said:**
> It seems to be a problem with the DNS. I can't figure out how a firefox replacement could affect this. Do you use a router?

Yes I do use a router. I doubt that the router would affect this. However, I do have Ubuntu configured as static IP in networking. I cannot change that because I need the static IP in my WLAN.

Also, other computers on the network doesn't seemed to be affected (Windows/Ubuntu)

---

### Post by lovinglinux on 2009-07-12
You could try the **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

Nevertheless, there is a similar discussion [here](http://ubuntuforums.org/showthread.php?p=7504203) that ended without solution.

---

### Post by Kraut~salat on 2009-07-12
1. You should check if it is a problem with Firefox or DNS. Do that by trying to ping [www.google.com](www.google.com) from a terminal. If you get a reply it is a firefox problem. If you do not get a reply check /etc/resolv.conf. There should be a "nameserver" entry in there. If there is no entry your router does not assign a nameserver. Try adding a manual entry to resolv.conf:
nameserver <your router IP here>

with many routers it is

nameserver 192.168.0.1

2. If you already have a nameserver entry and pinging from console works you have to check your firefox settings. Opeb firefox. click Edit->Preferences->Advanced. On the Network-tab click Settings. Try the "no proxy" setting or the "use system proxy"-setting.

Btw: you usually can configure your router in a way to always give your PC the IP-Adress. This is kind of having a static Adress, but also sets DNS and gateway setting automatically.

---

### Post by ultimatebuster on 2009-07-12
> **Kraut~salat said:**
> 1. You should check if it is a problem with Firefox or DNS. Do that by trying to ping [www.google.com](www.google.com) from a terminal. If you get a reply it is a firefox problem. If you do not get a reply check /etc/resolv.conf. There should be a "nameserver" entry in there. If there is no entry your router does not assign a nameserver. Try adding a manual entry to resolv.conf:
nameserver <your router IP here>

with many routers it is

nameserver 192.168.0.1

2. If you already have a nameserver entry and pinging from console works you have to check your firefox settings. Opeb firefox. click Edit->Preferences->Advanced. On the Network-tab click Settings. Try the "no proxy" setting or the "use system proxy"-setting.

Btw: you usually can configure your router in a way to always give your PC the IP-Adress. This is kind of having a static Adress, but also sets DNS and gateway setting automatically.

pinging is fine. Your firefox solution didn't work though.
I can't get the router to give my PC an IP address. It doesn't have that option. It's currently configured as DHCP.
Also, another computer configured to static IP works perfectly. No problem whatsoever.

---

### Post by lovinglinux on 2009-07-12
Try setting this in **about:config**

network.dns.disableIPv6;true
network.dnsCacheEntries;1000
network.dnsCacheExpiration;1800

---

### Post by ultimatebuster on 2009-07-13
> **lovinglinux said:**
> Try setting this in **about:config**

network.dns.disableIPv6;true
network.dnsCacheEntries;1000
network.dnsCacheExpiration;1800

It's been resolved, although I do not have network.dnsCacheEntries;1000 and network.dnsCacheExpiration;1800. But disabling IPv6 seemed to do the trick.

Thanks a lot!

---

### Post by lovinglinux on 2009-07-13
> **ultimatebuster said:**
> It's been resolved, although I do not have network.dnsCacheEntries;1000 and network.dnsCacheExpiration;1800. But disabling IPv6 seemed to do the trick.

Thanks a lot!

You are welcome. That's the **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

---

