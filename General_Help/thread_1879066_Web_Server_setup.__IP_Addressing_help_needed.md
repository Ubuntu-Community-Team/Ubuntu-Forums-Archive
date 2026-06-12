---
title: "Web Server setup.  IP Addressing help needed"
date: 2011-11-10
forum: General Help
---

### Post by zinnium on 2011-11-10
Ok.  I am planning to do a web server the following build instructions entitled:  "The Perfect Server - Ubuntu 11.10 [ISPConfig 3]"  from [http://www.howtoforge.com/perfect-server-ubuntu-11.10-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-11.10-ispconfig-3) .  This matched 90% of my original designed build and liked it. 

I am quite comfortable with all the install process but how to deal with the Static IP address provided by my Data Center I am Co-locating with.

I have the following from my data center:
1.   5 IP address
2.   1 Subnet
3.   1 Gateway
3.   2 DNS numbers.

The instructions contain a guide to setup only 1 IP address along with only one Name Server.  That is located on page 3 of the guide.  [http://www.howtoforge.com/perfect-server-ubuntu-11.10-ispconfig-3-p3](http://www.howtoforge.com/perfect-server-ubuntu-11.10-ispconfig-3-p3)

My question is how would I setup for the other IP addresses and adding a 2nd name server?  Or am I all backwards on this?   

This is one of the few things seeming to be missing from a lot of guides.

---

### Post by SeijiSensei on 2011-11-11
Are you planning on actually using the other addresses?  If so, you can use aliasing of the Ethernet interface.  If the primary interface is eth0, you can create additional virtual interfaces with names like eth0:0, eth0:1, etc., and assign them separate IP addresses.  See [this thread](http://ubuntuforums.org/showthread.php?t=1870364) for details.

These days there are few reasons to use multiple IPs on a single machine.  Name-based virtual hosting lets you assign an essentially unlimited number of web sites to a single IP.  I've used aliasing in cases where I wanted the machine to respond to different hostnames (e.g., mail.example.com and [www.example.com](www.example.com)) with different firewalling rules applied, or when I wanted to host both a secure and an insecure website on the same box.

There's no reason to run multiple nameservers either, except in some arcane cases.  A single instance of BIND9 can host the records for as many domains as you want.  If you're looking to use a second IP as a method of creating a DNS secondary, that's not a good idea.  If the box falls over, you'll lose both the primary and secondary.  The "best-practice" for DNS servers is to have the primary and secondary on separate machines, and preferably on entirely unrelated IP subnets.

Reading your post again, I think you have a misunderstanding about the "DNS numbers" you received from the hosting provider.  Those are likely the addresses of the ISP's DNS servers; they would be entered in /etc/resolv.conf.  If you want to run your own nameserver, you'd use those addresses as backups in resolv.conf like this:

```

domain example.com
nameserver 127.0.0.1
nameserver 8.8.8.8
nameserver 8.8.4.4

```

That tells the DNS resolver to use the local DNS server on the "localhost" address of 127.0.0.1.  If that server is unavailable, it tries the remaining nameserver entries until it finds one that replies.

---

