---
title: "name resolution failing"
date: 2006-01-29
forum: General Help
---

### Post by aultac on 2006-01-29
I just installed breezy on a new box.  I can ping IP addresses, but not domain names, and I can't figure out why.  Any help would be greatly appreciated, both by me and by the few hairs left on my scalp :).  

Here is the setup:
- Ubuntu box is wired to Linksys WRTG54G wireless router
- one windows computer is wired to the same router, and it works fine
- 2 laptops connect wirelessly to the router, both Mac's, and both are fine
- Ubuntu box gets IP address, gateway, DNS correctly from the router.  /etc/resolv.conf matches on the Ubuntu box and the Macs
- Ubuntu box can ping IP addresses, both on LAN and externally
- Ubuntu box can ping both nameserver addresses in /etc/resolv.conf
- Ubuntu box cannot resolve any hostnames
- running "sudo tcpdump -X" shows no packets being sent or received during a ping request, except after the ping has terminated, then a few outgoing UDP:53 requests for the domain name show up, but no incoming replies.

Any suggestions?  I could really use some help on this one...

---

### Post by dcstar on 2006-01-29
[QUOTE=aultac]I just installed breezy on a new box.  I can ping IP addresses, but not domain names, and I can't figure out why.  Any help would be greatly appreciated, both by me and by the few hairs left on my scalp :).  
.......
Any suggestions?  I could really use some help on this one...[/QUOTE]
Show us the contents of resolv.conf, do a forum search on "IPv6" and how to disable it.

---

### Post by aultac on 2006-01-30
~:$ cat /etc/resolv.conf
search somedomain.com
nameserver aaa.aaa.aaa.aaa
nameserver bbb.bbb.bbb.bbb

(replaced actual values, obviously :)

I disabled IPv6 according to previous posts.  /etc/modprobe.d/aliases was changed:
~:$ cat /etc/modprobe.d/aliases | grep "net-pf-10"
alias net-pf-10 off
~:$ sudo shutdown -r now
...
~:$ ping 64.233.167.104
PING 64.233.167.104 (64.233.167.104) 56(84) bytes of data.
64 bytes from 64.233.167.104: icmp_seq=1 ttl=242 time=20.8 ms
64 bytes from 64.233.167.104: icmp_seq=2 ttl=242 time=33.7 ms

--- 64.233.167.104 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 20.882/27.292/33.702/6.410 ms
~:$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

Pinging the nameserver also still works.  

I should also point out, just to make sure ipv6 is disabled:
~:$ lsmod | grep "ipv6"
~:$

I appreciate the help.  Thanks!
Aaron

---

### Post by dcstar on 2006-01-30
[QUOTE=aultac]~:$ cat /etc/resolv.conf
search somedomain.com
nameserver aaa.aaa.aaa.aaa
nameserver bbb.bbb.bbb.bbb

(replaced actual values, obviously :)
.......[/QUOTE]
Comment our the "search" line and see if things change.

BTW, are your nameservers external, and do you have any firewalls which may be blocking outgoing UDP to Port 53?

You can test basic connectivity to your nameservers by:

nslookup
lserver aaa.aaa.aaa.aaa
"host-to-lookup" (you should get a response from the nameserver)

---

### Post by aultac on 2006-01-30
> **dcstar]Comment our the "search" line and see if things change.[/QUOTE]
removed search line, nothing changed

[QUOTE=dcstar]BTW, are your nameservers external, and do you have any firewalls which may be blocking outgoing UDP to Port 53?[/QUOTE]
nameservers are ISP's said:**
> You can test basic connectivity to your nameservers by:

nslookup
lserver aaa.aaa.aaa.aaa
"host-to-lookup" (you should get a response from the nameserver)
~:$nslookup
>lserver aaa.aaa.aaa.aaa
Default server: aaa.aaa.aaa.aaa
Address: aaa.aaa.aaa.aaa#53
>[www.google.com](www.google.com)
;; connection timed out; no servers could be reached

So, basically, I know the nameservers are up because I can ping them, there is no firewall blocking UDP 53 because all other computers on the same subnet can resolve names through them, DHCP is working because I get all the correct info from the router, the router port I'm plugged into is working because I can ping the IP's in the outside world, yet I have no name resolution :(.

Again, thanks for the help!
Aaron

---

### Post by dcstar on 2006-01-30
[QUOTE=aultac]r
........
So, basically, I know the nameservers are up because I can ping them, there is no firewall blocking UDP 53 because all other computers on the same subnet can resolve names through them, DHCP is working because I get all the correct info from the router, the router port I'm plugged into is working because I can ping the IP's in the outside world, yet I have no name resolution :(.

Again, thanks for the help!
Aaron[/QUOTE]
Look in you /var/log/syslog and messages log files and see if you can spot any error messages that may be relevant.

Perhaps something weird is happening with a process?

---

### Post by nickmcg on 2006-02-03
I have a similar problem, but with a netgear router, although I can ping machines outside, I can only ping machines on the lan by IP address.

All machines on the lan are wireless and configured by DHCP. I have a mix of windoze & Ubuntu computers.

Looking at the router, the win machines all show hteir host name against IP address, but the ubuntu computers show as 'UNKNOWN' against the allocated IP addresses.

I cannot ping the ubuntu machines by name from any computer, and from the win machines, I can ping other win machines, but not ubuntu machines by name.

I also have a wireless HP printer which the win machines can ping by name.

Has anyone any ideas? (yes, I have disabled IPv6, and the DNS settings are the same on all machines)

TIA

Nick

---

### Post by hajk on 2006-02-03
Y'all say that their is no firewall problem, but I can only suggest that you look once more... the nameserver:tcp and/or udp port 53 must be open for name resolution to work on your Ubuntu box... I tore just about my very last hair out before solving a similar problem on my laptop's wireless connection that way.

---

### Post by nickmcg on 2006-02-03
So why is name resolution working on the wan, but not the lan?

I'm writing this on my ubuntu machine, but it cannot resolve the names of machines on the lan (and the router cannot determine the host name of this machine).

Is there somethng I need to do to open port 53 on this machine?

TIA

Nick

---

### Post by aultac on 2006-02-14
I finally figured out my problem.  Thanks to everyone who helped!

For some reason, when I get a DHCP address from my Linksys router (just as all the other interfaces on my network do), name resolution does not work.  I tried with Hoary, Breezy, and my old standard, Gentoo.  

Then, I remembered that when I setup my printer, the router wouldn't allow me to statically map a MAC to and IP (who writes a DHCP server without the ability to statically map IP's?).  So, I just manually set an IP address on the printer outside of the DHCP range with the router as the gateway, and all was well.

I figured it was worth a shot to try the same thing while I had the Gentoo live CD up.  I setup eth0 with a manual IP address that is outside the range of DHCP addresses on the router, and viola!  Everything works!

I still had my original Breezy install on the hard drives, so I booted back into breezy, did the same thing, and it worked too.  After 2 weeks of hair pulling, I just noticed the sun was out today :).

Thanks again for all the help.

Aaron

---

