---
title: "Network problem"
date: 2006-05-23
forum: General Help
---

### Post by W. Irving on 2006-05-23
The WiFi connection on my laptop seems to "sleep" after two minutes (did a quick measure - it's between 1.5 and 2 minutes) of inactivity. At this point, the computer stops responding to any incoming connection.

For example, if I ping it from my desktop computer (on the same network), the laptop does not respond..

```
Request timed out.
Request timed out.
Request timed out.
Reply from 192.168.1.5: bytes=32 time=582ms TTL=64
Reply from 192.168.1.5: bytes=32 time=1ms TTL=64
Reply from 192.168.1.5: bytes=32 time<1ms TTL=64
Reply from 192.168.1.5: bytes=32 time=1ms TTL=64
Reply from 192.168.1.5: bytes=32 time=1ms TTL=64
```

..until I ping the desktop from my laptop!

I don't have to run ifdown/ifup on the interface to get it going, just pinging or connecting to the computer that is attempting to connect to the laptop is enough.

How do I resolve this?

---

### Post by ????? on 2006-05-23
Are you using it through ndiswrapper?

---

### Post by W. Irving on 2006-05-23
No. I'm fairly sure I am using madwifi, through wpa_supplicant.

---

### Post by W. Irving on 2006-05-24
I like to add that I have no problems with the network in Windows XP, so the card itself is doing well.

I was hoping there'd be a log file somewhere of what the network interfaces are up to. Any ideas?

---

### Post by W. Irving on 2006-05-24
The only way I can maintain a connection between the two computers is if I run
```
ping -t 192.168.1.5
```
on my desktop PC running Windows.

This is really annoying! Please help! I don't even know where to start troubleshooting.

---

