---
title: "ntp not updating"
date: 2012-07-15
forum: General Help
---

### Post by holiday on 2012-07-15
I noticed that my system time was off so checking the config I saw that the time setting had fallen back to manual. 

I adjusted the GUI config and then started the conversation below

It looks like the ntp server is holding the ntp socket so that the ntp client cannot complete. I don't need an ntp server. It's the client I want. 

I may be misinterpreting. 

Can anyone shed light here? Offer advice.

Thanks

<code>
root@hp:/home/blink# ntpdate ntp.ubuntu.com
15 Jul 11:43:52 ntpdate[3801]: the NTP socket is in use, exiting
root@hp:/home/blink# /etc/init.d/ntp status
 * NTP server is running
root@hp:/home/blink# /etc/init.d/ntp restart
 * Stopping NTP server ntpd                                              [ OK ] 
 * Starting NTP server ntpd                                              [ OK ] 
root@hp:/home/blink# ntpdate ntp.ubuntu.com
15 Jul 12:32:18 ntpdate[4050]: the NTP socket is in use, exiting
root@hp:/home/blink# /etc/init.d/ntp stop
 * Stopping NTP server ntpd                                              [ OK ] 
root@hp:/home/blink# ntpdate ntp.ubuntu.com
15 Jul 12:32:41 ntpdate[4067]: adjust time server 91.189.94.4 offset 0.007749 sec
</code>

---

### Post by Cheesehead on 2012-07-15
Years ago, NTP used separate clients and servers. No longer. ntpd does both automatically.

Please post you /etc/ntp.conf file here.

---

### Post by holiday on 2012-07-15
Thanks for your response, CH

Here it is


# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help

driftfile /var/lib/ntp/ntp.drift


# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).


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
server time.nrc.ca 
server ntp1.cs.wisc.edu
server ntp1.cmc.ec.gc.ca
server ntp2.cmc.ec.gc.ca
server wuarchive.wustl.edu
server clock.psu.edu
server gilbreth.ecn.purdue.edu

---

### Post by Cheesehead on 2012-07-15
Ok, you certainly have a bunch of servers to listen to. Good.
Next, try the command [FONT="Courier New"]ntpq -p[/FONT] and post the result here.

```
$ ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*adsl-68-248-226 204.235.61.9     3 u  282 1024  377    0.408   -5.922   7.852
+slackadelic.com 164.244.221.197  2 u  855 1024  377   23.662   -3.501  13.980
+linode.curby.ne 173.10.246.233   2 u  892 1024  377   46.489  -13.451  13.473
+helium.constant 129.7.1.66       2 u  666 1024  377   35.808   -9.195   5.725
+ec2-174-129-25- 50.77.217.185    2 u  788 1024  377   40.596   -9.908  14.360

```
In this example,the "*" server is primary, and the "+" servers are active, servers get polled avery 1024 seconds, etc. 

Let's see what yours looks like.

---

### Post by holiday on 2012-07-16
Thanks!

     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 time.nrc.ca     132.246.11.232   2 u    6   64    1   74.295  100.954   0.001
 caesar.cs.wisc. 128.105.201.11   2 u    5   64    1   89.968  105.319   0.001
 dns1.cmc.ec.gc. 142.3.100.2      2 u    5   64    1   80.780  104.458   0.001
 dns2.cmc.ec.gc. .INIT.          16 u    -   64    0    0.000    0.000   0.000
 otc2.psu.edu    147.84.59.145    2 u    3   64    1  106.330  101.751   0.001
 gilbreth.ecn.pu .INIT.          16 u    -   64    0    0.000    0.000   0.000

---

### Post by Cheesehead on 2012-07-16
Hmmm. Looks like your NTP is getting time information every 64 seconds from a variety of sources...in other words, exactly what it's supposed to do.

Sorry, I'm out of ideas here. NTP is talking to other servers, so I don't know why it's not keeping time properly.

---

