---
title: "I need clarification on changing Ubuntu Linux PC name!"
date: 2009-12-04
forum: General Help
---

### Post by Rytron on 2009-12-04
Hi.
I just need some clarification regarding changing a computer name in Ubuntu Linux.

The guide I have is like so:

[I][B]gksudo gedit /etc/hosts /etc/hostname
Edit hostname first, then hosts and save both.
Reboot[/B][/I]

I understand that I simply overwrite the single name in /etc/hostname
In gedit /etc/hosts there are a few entries.

This is my /etc/hosts

[COLOR="DarkOrange"]127.0.0.1 NewPCName localhost.localdomain	localhost
127.0.1.1 NewPCName

# The following lines are desirable for IPv6 capable hosts
::1 localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/COLOR]

Do I need the line: 127.0.1.1 NewPCName? As far as I can remember there was no 127.0.1.1 line in the original /etc/hosts

---

### Post by scouser73 on 2009-12-04
> **Rytron said:**
> Hi.
I just need some clarification regarding changing a computer name in Ubuntu Linux.

The guide I have is like so:

[I][B]gksudo gedit /etc/hosts /etc/hostname
Edit hostname first, then hosts and save both.
Reboot[/B][/I]

I understand that I simply overwrite the single name in /etc/hostname
In gedit /etc/hosts there are a few entries.

This is my /etc/hosts

[COLOR="DarkOrange"]127.0.0.1 NewPCName localhost.localdomain	localhost
127.0.1.1 NewPCName

# The following lines are desirable for IPv6 capable hosts
::1 localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/COLOR]

Do I need the line: 127.0.1.1 NewPCName? As far as I can remember there was no 127.0.1.1 line in the original /etc/hosts

Check this tutorial: [[COLOR="Red"]**Ubuntu: Changing Hostname**[/COLOR]]("http://sysblogd.wordpress.com/2008/05/16/ubuntu-changing-hostname-from-command-line/")

---

### Post by sisco311 on 2009-12-04
/etc/hostname:
```
NewPCName
```

/etc/hosts:
```
127.0.0.1 localhost.localdomain localhost
127.0.1.1 NewPCName

# The following lines are desirable for IPv6 capable hosts
...
```


*The most commonly used IP address on the loopback device is 127.0.0.1 for IPv4, although any address in the range 127.0.0.0 to 127.255.255.255 is mapped to it.* ~ [http://en.wikipedia.org/wiki/Loopback#Virtual_network_interface]("http://en.wikipedia.org/wiki/Loopback#Virtual_network_interface")

So both 127.0.0.1 and 127.0.1.1 is the local machine.

*The  host  name  is   usually   set   once   at   system   startup   in /etc/rc.d/rc.inet1  or  /etc/init.d/boot  (normally by reading the contents of a file which contains the host name, e.g.  /etc/hostname).*
~ man hostname 

[i]The UNIX hostname should be written
into /etc/hosts always on its own line, never as an alias for
'localhost.localdomain'.  If there is no fixed NIC with a permanent IP
address then the UNIX hostname should be put on a line

[INDENT]127.0.1.1  <hostname>[/indent]

That will ensure that if the UNIX hostname _is_ resolved then it will
always be its own canonical hostname
(in the sense of hosts(5))[/i] ~ [http://lists.debian.org/debian-boot/2005/06/msg00938.html]("http://lists.debian.org/debian-boot/2005/06/msg00938.html")

---

### Post by Iowan on 2009-12-04
Probably redundant, but I prefer to leave 127.0.0.1 as localhost (and maybe localhost.local), and edit 127.0.1.1 as the hostname.

---

### Post by Rytron on 2009-12-05
Thank you all.

---

