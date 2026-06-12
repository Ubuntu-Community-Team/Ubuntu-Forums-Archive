---
title: "installed dhcp-3 and firestarter but ?"
date: 2006-02-07
forum: General Help
---

### Post by petef on 2006-02-07
Hi guys

I installed Firestarter and DHCP-3 as per below thread on Breezy but how do I know I have DHCP running ? 

[http://www.ubuntuforums.org/showthread.php?t=74925&highlight=installed+firestarter+dhcp](http://www.ubuntuforums.org/showthread.php?t=74925&highlight=installed+firestarter+dhcp)

If I do ifconfig I can see I have a static IP.

Using a Linksys wireless card. Not sure if Firestarter is working with DHCP ?

Thanks in advance.

Pete

---

### Post by ninotob on 2006-02-08
what does your network look like?  Sometimes it's just easier to use static IPs.  For example at home, I have:

cable_modem ----> firewall ---->wireless_router----->wired and wireless machines.

Rather than mess w/ DHCP server on the firewall, I just set the inside card manually and the wireless router's IP manually.  The router dishes out DHCP addresses to the various machines attached to it.  At work, I don't have any dynamic IPs at all -- everything is static and it makes it so much easier for me because I don't have to lookup a machine's IP when I want to ssh into it, and I can see who is doing what really easily.   The only snafu that might not be immediately apparent is that you also need to manually identify the DNS servers your ISP provides.  Even if everything is perfectly set up, if you aren't pointed at a DNS server you can't really get anywhere on the net, at least not by name address.

---

### Post by ninotob on 2006-02-08
let me answer your actual question!  ;-)

How to know if dhcpd is running:
ps -e | grep dhcp

You should see a process called "dhcpd" (or similar)

---

