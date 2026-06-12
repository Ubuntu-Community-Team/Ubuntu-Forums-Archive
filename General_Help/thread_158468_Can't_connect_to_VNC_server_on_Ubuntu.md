---
title: "Can't connect to VNC server on Ubuntu"
date: 2006-04-11
forum: General Help
---

### Post by W. Irving on 2006-04-11
I am using 5.10 on my laptop, planning on migrating from XP completely.
But I can't connect to VNC on this machine, I've tried both the built in VNC server thought System->Preferences->Remote Desktop as well as vnc4server available through Universe (took some fiddling with font paths, but I figured it out eventually :)).

The problem is always the same; using VNC viewer (or a browser, using port 5800), I can't connect to the VNC server on Ubuntu.

Have done this:

- connecting locally, using **vncviewer localhost** (or specifying IP address and port number). Success!
- telnet:ing locally on port 5900/5901. Success!
- connecting from another PC using VNC viewer in Windows: "Connection timed out"..
- telnet:ing from a Windows PC on port 5900/5901. Says "Could not open connection to the host"
- running **netstat -l** on the laptop, reports *:5901 or *:5900 (depending on which VNC server I use)
- starting VNC server on Windows PC, using vncviewer on laptop to connect to it using IP #. Success.

I am not running any firewalls on the laptop (that I'm aware of). I did install Firestarter, but stopped + closed it when I ran into trouble.
The laptop has a WiFi card, connected to the router (to which the Windows PC is connected via Ethernet), and the Internet connection works well. If i enter the IP # of the Windows PC into Firefox on the laptop, Apache happily serves my dev site.

It's evident something on my laptop is sending calls that don't originate at localhost to /dev/null
Browsing thes forums, I've realised I'm not the only one with this problem. So what's wrong?

---

### Post by W. Irving on 2006-04-11
The laptop does not responde to remote ping's either (local pings are ok).

Any ideas? Clues? Please? :)

---

### Post by cskeide on 2006-04-11
[QUOTE=W. Irving]The laptop does not responde to remote ping's either (local pings are ok).

Any ideas? Clues? Please? :)[/QUOTE]
sounds to me that there's a firewall running on your system. have you tried issuing iptables -L? If your not running a firewall the output should be something like this:
```
user@localhost:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

---

### Post by W. Irving on 2006-04-11
[QUOTE=cskeide]sounds to me that there's a firewall running on your system. have you tried issuing iptables -L? If your not running a firewall the output should be something like this:
```
user@localhost:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```[/QUOTE]

Thanks for the reply!
Iptables -L returns the following:

```
Chain INBOUND (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
LSI        all  --  anywhere             anywhere

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  192.168.1.1          anywhere            tcp flags:!SYN,RST,ACK/SYN
ACCEPT     udp  --  192.168.1.1          anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
DROP       all  --  anywhere             255.255.255.255
DROP       all  --  anywhere             192.168.1.255
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5
INBOUND    all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward'

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (2 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       icmp --  anywhere             anywhere            icmp echo-request
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '
DROP       all  --  anywhere             anywhere

Chain LSO (0 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  192.168.1.8          192.168.1.1         tcp dpt:domain
ACCEPT     udp  --  192.168.1.8          192.168.1.1         udp dpt:domain
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
OUTBOUND   all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output'

```

I've been looking at this before, but the learning curve is *rather* steep. It seems ok though, doesn't it? Firestarter is indeed installed, but it isn't running. At least, I assume it isn't, since the Firestarter icon is not present on the panel.

---

### Post by cskeide on 2006-04-11
I'm afraid firestarter is indeed running. Firestarter starts automatically at boot. The fact that the icon isn't visible on your desktop does not mean that it is stopped.

To stop firestarter, issue the following in a terminal:
```
sudo /etc/init.d/firestarter stop
```

To stop firestarter from starting at boot-time, issue the following:
```
sudo update-rc.d -f firestarter remove
```

Hope this solves your problem.

---

### Post by W. Irving on 2006-04-11
I have tried connecting while having the Firestarter GUI open, and clicking Stop Firewall. Anyway, issued the stop command, and attempted connecting once more.
No difference (yup, confirmed the server was running by connecting locally, and checking it's listening on the right port using netstat -l).
The laptop still doesn't respond to ping.

However, iptables -L now returns the three empty tables you displayed in your first post.


EDIT: This is really strange. To confirm I was attempting to connet to the correct IP address, I once again connected from the laptop to Apache running on my desktop, and pulled the laptop IP address from the Apache access log on my desktop PC, and it worked!

```


C:\Documents and Settings\E>ping 192.168.1.8

Pinging 192.168.1.8 with 32 bytes of data:

Request timed out.
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 192.168.1.8:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),

**<this is where I visited my dev site on the desktop>**

C:\Documents and Settings\E>ping 192.168.1.8

Pinging 192.168.1.8 with 32 bytes of data:

Reply from 192.168.1.8: bytes=32 time=1ms TTL=64
Reply from 192.168.1.8: bytes=32 time=1ms TTL=64
Reply from 192.168.1.8: bytes=32 time=1ms TTL=64
Reply from 192.168.1.8: bytes=32 time=1ms TTL=64

Ping statistics for 192.168.1.8:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 1ms, Maximum = 1ms, Average = 1ms
```

Madness! Looks like Ubuntu needs to 'validate' the changes done by iptables somehow.

Thanks for the help cskeide!

---

