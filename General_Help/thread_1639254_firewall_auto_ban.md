---
title: "firewall auto ban?"
date: 2010-12-06
forum: General Help
---

### Post by sohlinux on 2010-12-06
How can I set the firewall to automatically ban an ip address when it scans my computer? something similar to configserver firewall for whm.

---

### Post by mcduck on 2010-12-06
If you want that kind of features, you might want to try Arno's Iptables Firewall:

[http://rocky.eld.leidenuniv.nl/joomla/index.php?option=com_content&view=article&id=45&Itemid=63]("http://rocky.eld.leidenuniv.nl/joomla/index.php?option=com_content&view=article&id=45&Itemid=63")

It's pretty awesome, I used to have cool configuration that instead of immediate banning would start randomly rejecting, dropping or sending the packages back. I bet that would have been a bit confusing to anybody trying to scan the machine... ;) (then I realized that I don't actually need a firewall at all, so much for that fun.)

edit:
Features:
    * Very secure stateful filtering firewall
    * Both kernel 2.4 & 2.6 support
    * It can be used for both single- and multi(eg. dual)-homed boxes
    * Masquerading (NAT) and SNAT support
    * (Experimental) IPv6 support (IPv4 / IPv6 mixed mode support in 1.9.9 or better)
    * Multiple external (internet) interfaces
    * Support multiroute NAT & SNAT (load balancing over multiple (internet) interfaces)
    * Port forwarding (NAT)
    * Support MAC address filtering
    * Support for static and ISP assigned (DHCP) IPs
    * Support for (transparent) proxies
    * Full support for DMZ's and DMZ-2-LAN forwarding. You can also use it to isolate your eg. wireless LAN.
    * (Nmap)(stealth) portscan detection
    * Protection against SYN-flooding (DoS attacks)
    * Protection against ICMP-flooding (DoS attacks)
    * Extensive user-definable logging with rate limiting to prevent log flooding
    * Includes options to optimize your throughput
    * User definable open ports, closed ports, trusted hosts, blocked hosts etc.
    * Log & protection options are both highly customizable
    * Support for custom iptables rules in a seperate file
    * It can be used with chkconfig runlevel system (eg. RedHat/Fedora)
    * Main focus on TCP/UDP/ICMP but additional support for *ALL* IP protocols
    * Plugin support (to add extra features).
    * SSH Brute Force (Cracking) Protection (plugin)
    * DynDNS (Dynamic DNS) support (plugin)
    * Intrusion Detection System (IDS) (plugin)
    * Traffic Shaping (plugin)
    * SIP/VOIP support (plugin)
    * Traffic Accounting support (plugin)
    * IPSEC support (plugin)
    * Support for DSL/ADSL modems, supporting PPPoE, PPPoA and bridging modem setups  (plugin)
    * It works with PoPTop PPTP ([http://www.poptop.org](http://www.poptop.org))
    * It works with UPnP
    * DRDOS protection/detection (experimental)
    * It's easy to install & configure
    * And much more...

---

### Post by sohlinux on 2010-12-06
perfect! just what I need! ;) hey everyone needs a firewall

---

