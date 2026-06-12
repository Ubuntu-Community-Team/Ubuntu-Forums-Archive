---
title: "firestarter event question"
date: 2010-02-02
forum: General Help
---

### Post by brusegadi on 2010-02-02
Possibly paranoid, should I be concerned about firestarter displaying a connection to:

ec2-<IP ADDRESS>-.compute-1.amazonaws.com
Port 443
Service HTTPS
Program Python

I just have no idea whats running that connection...  Thanks!!

---

### Post by 3rdalbum on 2010-02-02
Firestarter tends to make people paranoid.

If it's an incoming connection, then check the settings of your outermost firewall (the one on your modem, if you have one). If it's an outgoing connection, then it's probably nothing to worry about - Ubuntu is designed to integrate with virtual computing services on Amazon.

---

### Post by Ordes on 2010-05-04
i have the same connection.. i think it is legit.. but i still wonder for what and why python creates this con....

---

### Post by byronical on 2010-05-30
I had the same concerns but after some investigation it appears that this is used by the Ubuntu One Sync Daemon

```
byronical[~]: netstat -ntp | grep ":443"
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp       38      0 192.168.1.2:57604       91.189.89.219:443       CLOSE_WAIT  4692/python     
tcp       38      0 192.168.1.2:50220       91.189.89.59:443        CLOSE_WAIT  5144/python     
tcp       38      0 192.168.1.2:60680       91.189.89.212:443       CLOSE_WAIT  5144/python     
tcp        0      0 192.168.1.2:49479       174.129.193.12:443      ESTABLISHED 4692/python     
byronical[~]: ps -f -p 4692
UID        PID  PPID  C STIME TTY          TIME CMD
1000      4692     1  0 17:15 ?        00:00:28 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
byronical[~]:
```

---

