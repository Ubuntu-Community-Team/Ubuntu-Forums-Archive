---
title: "Execute file at STARTUP - init.d (HOW)"
date: 2011-05-24
forum: General Help
---

### Post by lordbux on 2011-05-24
I want a set of command file to execute when the system starts up.

I wrote the following commands in a file called ==> FIREWALL
```
#!/bin/bash

#clear all data
iptables -F
iptables -X

#set status
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -p tcp -m tcp --dport 80  -j ACCEPT
iptables -A INPUT -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT

#dns
iptables -A INPUT -p udp -m udp --sport 53 -j ACCEPT
iptables -A OUTPUT -p udp -m udp --dport 53 -j ACCEPT
iptables -A INPUT -p tcp -m tcp --sport 53  -j ACCEPT
iptables -A OUTPUT -p tcp  -m tcp --dport 53  -j ACCEPT

#torrent
iptables -A INPUT -p tcp -m tcp --dport 6881:6889 -j ACCEPT

#Squid Redirection
iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner squid -j ACCEPT
iptables -t nat -A OUTPUT -p tcp --dport 3128 -m owner --uid-owner squid -j ACCEPT

iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner grandmaster  -j ACCEPT

iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-ports 8080

iptables -t nat -A OUTPUT -p tcp --dport 3128 -j REDIRECT --to-ports 8080

squid
dansguardian
dansguardian -g
```

Then made it executable ```
chmod +x ./FIREWALL
```
Then changed the Ownership to root ```
chown root:root ./FIREWALL
```

Than copied it to > /etc/init.d/

Still It does not run at start up
Please help
Thank you in advance

---

### Post by hwttdz on 2011-05-24
I might put the script in root's bin (/root/bin) and then add a call to the script in /etc/rc.local

---

### Post by conradin on 2011-05-24
use ufw (comes with ubuntu)
```
sudo ufw enable
```
then your firewall will be enabled at boot.
you can edit the configure files how ever you want, Ive found ufw is pretty simple compared to iptables

---

### Post by lordbux on 2011-05-26
> **conradin said:**
> use ufw (comes with ubuntu)
```
sudo ufw enable
```
then your firewall will be enabled at boot.
you can edit the configure files how ever you want, Ive found ufw is pretty simple compared to iptables

Sorry UFW wont work for me, I need more advanced options that can be only linked by Iptables commandline.

---

### Post by lordbux on 2011-05-26
> **hwttdz said:**
> I might put the script in root's bin (/root/bin) and then add a call to the script in /etc/rc.local

Did not help, no change the script does not run

---

### Post by 5149.5 on 2011-05-26
Have you tried it with the script in init.d and a link to the script in rcS.d?

---

### Post by lordbux on 2011-06-12
> **5149.5 said:**
> Have you tried it with the script in init.d and a link to the script in rcS.d?

NOT WORKING, this problem is giving lot of trouble.
any one know any solutions, because file in /ete/init.d 
is not executing by itself

---

### Post by lordbux on 2011-06-13
> **lordbux said:**
> not working, this problem is giving lot of trouble.
Any one know any solutions, because file in /ete/init.d 
is not executing by itself


bump

---

### Post by Cheesehead on 2011-06-13
Three solutions:

**Solution #1: Complicated and obsolete.**
If you **really** want it at startup, and you **really** want to use the old sysvinit mechanism, then:

1) Put the file in /etc/init.d/,, with an LSB header specifying the servicename.
2) Symlink it to the runlevels using the 'update-rc.d <servicename> start 2345' command.


**Solution #2: Easiest**
You don't really need the script to run at startup - there are no network connections yet...you need it to run when a network interface gets configured and comes up. 

Put the firewall script in (or link to) **/etc/network/if-up.d/** . Everything in that folder gets run when an interface comes up using 'ifup' or Network Manager. That's how I run my server firewall, for example.


**Solution #3: Geekiest**
The old sysvinit system was superseded a couple years ago by Upstart. You can see the Upstart scripts in /etc/init/ . Upstart uses Events to figure out what to start and stop...and 'net-device-up'/'net-device-down' emitted by ifup/ifdown (and Network Manager) happens to already be set up for you.

An Upstart listener for 'net-device-up' can also run the firewall script.

---

