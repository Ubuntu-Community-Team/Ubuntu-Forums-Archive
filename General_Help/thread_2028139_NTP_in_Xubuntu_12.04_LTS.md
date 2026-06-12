---
title: "NTP in Xubuntu 12.04 LTS"
date: 2012-07-17
forum: General Help
---

### Post by Marzata on 2012-07-17
NTP (Network Time Protocol) is installed but it is not working in Xubuntu 12.04 LTS. How to make it work? Thank you.

---

### Post by Cheesehead on 2012-07-17
How can you tell that it's not working?

Please paste your /etc/ntp.conf here.

Please ppen a termninal, try the command [FONT="Courier New"]ntpq -p[/FONT] and paste the result here.

---

### Post by Marzata on 2012-07-19
It is not working because [http://time.is/](http://time.is/) shows the following:  
"Your clock is 1.0 seconds ahead.
Accuracy of synchronization was ±0.023 seconds."

Here is /etc/ntp.conf content: 

```

# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help

driftfile /var/lib/ntp/ntp.drift


# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable

# Specify one or more NTP servers.

# Use servers from the NTP Pool Project. Approved by Ubuntu Technical Board
# on 2011-02-08 (LP: #104525). See http://www.pool.ntp.org/join.html for
# more information.
server 0.ubuntu.pool.ntp.org
server 1.ubuntu.pool.ntp.org
server 2.ubuntu.pool.ntp.org
server 3.ubuntu.pool.ntp.org

# Use Ubuntu's ntp server as a fallback.
server ntp.ubuntu.com
server time.isnet.is

# Access control configuration; see /usr/share/doc/ntp-doc/html/accopt.html for
# details.  The web page <http://support.ntp.org/bin/view/Support/AccessRestrictions>
# might also be helpful.
#
# Note that "restrict" applies to both servers and clients, so a configuration
# that might be intended to block requests from certain clients could also end
# up blocking replies from your own upstream servers.

# By default, exchange time with everybody, but don't allow configuration.
restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1
restrict ::1

# Clients from this (example!) subnet have unlimited access, but only if
# cryptographically authenticated.
#restrict 192.168.123.0 mask 255.255.255.0 notrust


# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
#broadcast 192.168.123.255

# If you want to listen to time broadcasts on your local subnet, de-comment the
# next lines.  Please do this only if you trust everybody on the network!
#disable auth
#broadcastclient
```

Here is the output of ntpq -p: 

```
user@host:~$ ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 ntp.sunflower.c .INIT.          16 u    - 1024    0    0.000    0.000   0.000
 tick.tadatv.com .INIT.          16 u    - 1024    0    0.000    0.000   0.000
 ponderosa.piney .INIT.          16 u    - 1024    0    0.000    0.000   0.000
 triangle.kansas .INIT.          16 u    - 1024    0    0.000    0.000   0.000
 europium.canoni .INIT.          16 u    - 1024    0    0.000    0.000   0.000
 time.c.is       .INIT.          16 u    - 1024    0    0.000    0.000   0.000

```

---

### Post by lightning slinger on 2012-07-20
Don't forget NTP requires UDP access on port 123! Check that you have allowed UDP Out on port 123 on the firewall!

---

### Post by Cheesehead on 2012-07-20
> **Marzata said:**
> Here is the output of ntpq -p: 

```
user@host:~$ ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 ntp.sunflower.c .INIT.          16 u    - 1024    0    0.000    0.000   0.000
 tick.tadatv.com .INIT.          16 u    - 1024    0    0.000    0.000   0.000
 ponderosa.piney .INIT.          16 u    - 1024    0    0.000    0.000   0.000
 triangle.kansas .INIT.          16 u    - 1024    0    0.000    0.000   0.000
 europium.canoni .INIT.          16 u    - 1024    0    0.000    0.000   0.000
 time.c.is       .INIT.          16 u    - 1024    0    0.000    0.000   0.000

```

lightning slinger is right.

Your ntp.conf looks normal.
Your ntpq shows that ntp is trying to connect to each pool server regularly, but has never successfully connected. The most common reason for that is a firewall blocking the port.

---

### Post by Marzata on 2012-07-20
I have not installed any firewall. How to fix that ntp problem?

---

### Post by Cheesehead on 2012-07-20
Does the network seem to work properly for everything else?

Please paste the output from each of the following commands:
```
ps -e | grep ntp
sudo netstat -tulpn | grep ntp
iptables -L
```

The first will show if ntp is actually running.
The second will see if ntp is actually taking control of a port.
The third will see if ntp is blocked by Ubuntu's firewall.

Have you checked upstream? Perhaps an upstream router is blocking port 123? For example, some public internet cafes block most ports.

---

### Post by Marzata on 2012-07-20
When I do it manually it works. 

```
user@host:~$ sudo ntpdate -s -b -p 8 -u time.isnet.is
```

---

### Post by Marzata on 2012-07-20
```
user@host:~$ ps -e | grep ntp
20391 ?        00:00:01 ntpd

```

```
user@host:~$ sudo netstat -tulpn | grep ntp 
udp        0      0 192.168.7.100:123       0.0.0.0:*                           20391/ntpd      
udp        0      0 127.0.0.1:123           0.0.0.0:*                           20391/ntpd      
udp        0      0 0.0.0.0:123             0.0.0.0:*                           20391/ntpd      
udp6       0      0 ::1:123                 :::*                                20391/ntpd      
udp6       0      0 fe80::1a3d:a2ff:fe2:123 :::*                                20391/ntpd      
udp6       0      0 :::123                  :::*                                20391/ntpd 

```

```

user@host:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

```

---

### Post by Cheesehead on 2012-07-20
Well, those all look fine. NTP appears to be working properly on your machine. It seems unable to communicate with other machines, but that's apparently *not* Ubuntu's fault. All networking settings on your Ubuntu system are correct for NTP to work.

I recommend the NTP project's troubleshooting page: [http://support.ntp.org/bin/view/Support/TroubleshootingNTP#Section_9.5](http://support.ntp.org/bin/view/Support/TroubleshootingNTP#Section_9.5) . It has a very good step-by-step instructions

---

### Post by Marzata on 2012-07-28
So, any more idea how to make (fix) ntp working in Xubuntu 12.04 LTS? By the way is it working in Ubuntu 12.04 LTS?

---

### Post by Cheesehead on 2012-07-28
Well, I'm using ntp on Xubuntu 12.04, and mine is working fine.
Again, I can't find anything showing your ntp is *not* working fine. It's unable to connect to servers to sync - that's a network issue, not an ntp issue. 

Are you behind a router that blocks outbound port 123? (Like a LAN with an internal timeserver)
Otherwise, you can try reinstalling ntp.

---

### Post by Marzata on 2012-07-28
It works when I do
```
sudo ntpdate -s -b -p 8 -u time.isnet.is
```
so, the router is fine. 

Any more ideas?

---

