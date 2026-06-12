---
title: "Incorrect time Ubuntu 9.04"
date: 2010-09-21
forum: General Help
---

### Post by lavrentis on 2010-09-21
Hello,

The time on my server appears to be out but I am unsure how to set it correctly and keep it set.

I did the 'date' command in PuTTY and it showed the time as 6 infront behind of the correct time  (and the wrong time zone).

I am aware of ntp and I have tried to use it but it has not worked for me.

Please could you help me set the correct time and explain how to keep it correct without it drifting. Please can you be specific because I am new to this. ( I have Ubuntu 9.04)

Regards

---

### Post by lavrentis on 2010-09-22
Bump.

---

### Post by SlugSlug on 2010-09-22
sudo apt-get install ntp

&

and also sudo tzconfig

---

### Post by lavrentis on 2010-09-22
> **SlugSlug said:**
> sudo apt-get install ntp

&

and also sudo tzconfig

I did sudo tzconfig and I got this

> 
WARNING: the tzconfig command is deprecated, please use:
 dpkg-reconfigure tzdata


I then did sudo dpkg-reconfigure tzdata

Configured the time to my local time (London)

But the time is still 6 minutes out of the correct time.

---

### Post by SlugSlug on 2010-09-22
give it a reboot maybe..

I installed ntp on a load of our remote ftp servers..  some updated instantly - some took a few mins..

---

### Post by lavrentis on 2010-09-22
> **SlugSlug said:**
> give it a reboot maybe..

I installed ntp on a load of our remote ftp servers..  some updated instantly - some took a few mins..

sorry forgot to mention ntp was already installed. I restarted the server which didn't affect it.

Please could you give an example of a good ntp.conf because I think mine might be set incorrectly.

Thanks

---

### Post by SlugSlug on 2010-09-22
cat /etc/ntp.conf

```
 
# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help

driftfile /var/lib/ntp/ntp.drift


# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
server ntp.ubuntu.com 

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

cat /etc/default/ntpdate
```

# The settings in this file are used by the program ntpdate-debian, but not
# by the upstream program ntpdate.

# Set to "yes" to take the server list from /etc/ntp.conf, from package ntp,
# so you only have to keep it in one place.
NTPDATE_USE_NTP_CONF=yes

# List of NTP servers to use  (Separate multiple servers with spaces.)
# Not used if NTPDATE_USE_NTP_CONF is yes.
NTPSERVERS="ntp.ubuntu.com"

# Additional options to pass to ntpdate
NTPOPTIONS=""

```


cat /etc/default/ntp

```

NTPD_OPTS='-g'

```

---

