---
title: "Setup office network - dns, ldap, mail server?"
date: 2012-07-31
forum: General Help
---

### Post by ericmachine on 2012-07-31
Hi everyone,

I am new to setting up a proper environment for my office. 

Currently I have 2 servers; 1 for mail server and 1 for web server.

All these are running on Ubuntu 10.04 LTS 64 bits.

I have a LAN configured correctly with proper internet access (the switch supports VLAN500 to ensure internet stability). I have a router gateway at 192.168.1.1. Now my dns I am using Google DNS 8.8.8.8 and 8.8.4.4.

There's no firewall for now as I am still evaluating Sonicwall NSA2400.

Now I have few questions:-

a. My mail server as for now is zimbra.local. It is connected at 192.168.1.2. I can access this IP via my client desktop. But I prefer to enter [http://zimbra.local](http://zimbra.local) (or some nice name) to access this server. I think I need a DNS server, but how do I configure one? I still need to access 8.8.8.8 and 8.8.4.4 as it is much faster connecting to internet with these nameservers. I assume if I create my own DNS, all my desktops clients need to set this DNS manually. Note, all my client machines are on static IPs.

b. On the mail server, if someone sends email from hotmail or yahoo to my office email address. e.g. [EMAIL="eric@mycompany.com"]eric@mycompany.com[/EMAIL]. How do I configure my mail server to receive this? Even I setup a local DNS, it's still within the local area network. 

As for now my office internet comes with 1 static IP address. Do I need to have a separate IP address? 

For my office's domain e.g. mycompany.com, do I need to login to godaddy and change the nameservers and point to my company's DNS server? But my company DNS's servers (if created in point a), are all local IPs. 

Any tips to make the above works? So I can receive and send email (in and out of company, vice versa).

c. my servers are all ubuntu based. But my client desktops are all Mac based. I plan to get Apple Mountain Lion Server that has Open Directory. It can manage my Macs very well, but there's a problem. Not many firewall or (i think) the ubuntu servers can understand Open Directory. Should I setup an ubuntu LDAP or something? But can Macs (10 lions desktop and 1 mountain lion) understand Ubuntu LDAP?

d. i plan to setup some caching server. Looking at [http://www.squid-cache.org/](http://www.squid-cache.org/). But I am not sure how it comes into the picture? Should I have 1 server for this squid-cache. Is this something like proxy server where all desktop clients will configure? 

Any tutorials which I can read up for more information?

Any help from this community? Thanks in advance.

---

