---
title: "SSH timeout"
date: 2009-08-09
forum: General Help
---

### Post by Patricrawley on 2009-08-09
When I go to tunnel into my ssh server from a remote address I time out. Port 22 is forwarded to the correct internal ip address, what do I do?

---

### Post by ridgeland on 2009-08-09
I would try ping to make sure the other end is up and running.
If ping is OK I would delete ~/.ssh/known_hosts because that has caused problems for me when things change.
If the problem persists then tell us more... Was it working and stopped? Never worked?...  Do you have access to control files on both computers?

---

### Post by Patricrawley on 2009-08-09
I have access on the local network and it has never worked.

---

### Post by ridgeland on 2009-08-09
I use ssh to access to my Mom's PC, a friend's PC both remote IP and to my wife's PC here on the local network.  I once changed a setting on my Mom's PC that knocked me off her PC and I had to have a niece edit hosts.allow for me to get back on.
Tell me what you are doing... Simple PCs, Corporate world?  Connecting remotely to your own PC?  Is there a router and a modem? I'm guessing that you have a router and that you set it up to forward port 22 to the remote PC you are trying to connect to.
"it has never worked" suggests that it could be a simple setup step that needs changed.
Always times out suggests that the remote is down or ignoring the request, thus the check with ping.

---

### Post by Patricrawley on 2009-08-09
It's my second computer, I want to have it to back up my data while I'm at school. On my router I have it forwarded to the correct internal IP address and I can ssh tunnel into it on the lan. It responds to pings, it just always times out on tunneling in from an external. I know I have the correct IP address to.

---

### Post by ridgeland on 2009-08-09
Between you-remote location and you-home there can be firewalls that kill port 22.  Your work or school can kill the tunnel.  I've been retired for 10 years so I have no experience there.
You can test going from your home PC#1 to home PC#2 via the full IP address (not the lan address 192.168.123.123 or whatever).
Get your current IP address and ping it.
[http://www.ip-adress.com/](http://www.ip-adress.com/)
If ping passes then try the connection
ssh myID@123.123.123.123

---

### Post by Patricrawley on 2009-08-09
```
Pinging 71.50.176.44 with 32 bytes of data:
Reply from 71.50.176.44: bytes=32 time=2ms TTL=253
Reply from 71.50.176.44: bytes=32 time=2ms TTL=253
Reply from 71.50.176.44: bytes=32 time=2ms TTL=253
Reply from 71.50.176.44: bytes=32 time=2ms TTL=253

Ping statistics for 71.50.176.44:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 2ms, Maximum = 2ms, Average = 2ms

```

But connection refused in ssh

---

### Post by ridgeland on 2009-08-09
I just tried:
ssh root@71.50.176.44
result:
ssh: connect to host 71.50.176.44 port 22: Connection timed out
it's not replying.
It should ask me for a password then tell me that the connection was refused.  Not because I failed to guess root's password but because hosts.deny should always refuse remote root login.
This means the router is not forwarding your port 22.  Next step router setup.  Mostly likely culprit dynamic port assignment.  Do you have your port 22 forwarded to a fixed address that is always assigned to PC#2?  My router lets me assign a PC's MAC to a fixed port.  My Mom's router assigns port 22 to a fixed line (192.168.100.2) but dynamically assigns the lines to whichever PC powers up first.  How does your router handle this?

---

### Post by Patricrawley on 2009-08-09
I have it forwarded to the correct internal ip, and it assigns it by first sign on.

---

### Post by Patricrawley on 2009-08-10
I just switched to a static internal and I'm still having issues. I changed the port forwarding to match it as well.

---

### Post by ridgeland on 2009-08-10
Good morning,
One thing I should have mentioned earlier.
View /var/log/auth and /var/log/auth.0 on the PC running the server.  Find it in Nautilus since I may have a typo (no server up to check).
Scan through it with gedit, turn off line wrap.  Watch for lines that show things like:
Aug  3 14:10:45 ServerName sshd[7293]: Accepted password for myID from 74.220.13.245 port 6002 ssh2 
and:
Aug  5 10:05:19 ServerName sshd[7081]: refused connect from 126.128.56.190.static.intelnet.net.gt (::ffff:190.56.128.126) 

It could be that your /etc/hosts.allow and /etc/hosts.deny are blocking the outside world.  Post the contents (without #comment lines) of those two files.

---

### Post by Patricrawley on 2009-08-10
Both of theose files, /etc/hosts.allow and /etc/hosts.deny, are empty.

---

### Post by ridgeland on 2009-08-10
On my Mom's PC /etc/hosts.allow has
ALL: .chibardun.net
ALL: 74.220.
ALL: 216.41.

/etc/hosts.deny has:
ALL: ALL

You'll find the web-bots attack your ssh host big time.  They connect then play the guessing game of user+password.  The above says only IPs that are .chibardun.net (my local phone company) or 74.220. and 216.41. can connect.  Those last two are the only IPs I've see Chibardun use.  The result is every web-bot not here gets "connection refused".

/etc/ssh/sshd_config has:
Port 22
Protocol 2
AllowUsers ridgeland2c4toHelp
PermitRootLogin no

This tells it only one user can log in (me) and that user has a very hard to guess User ID.  I also use a Pubkey of 2048 characters rather than a password.  So only one user can connect, that user ID looks like a password, then it uses a Pubkey that would be very hard to crack.

I'm still curious what you found in auth.log
On my Mom's PC I run a script with:
cat /var/log/auth.log | grep password
cat /var/log/auth.log | grep refused
cat /var/log/auth.log | 'session opened'

---

### Post by Patricrawley on 2009-08-10
In the auth.log the only entries were the one's where I was on the local network. Nothing refused.

---

### Post by Patricrawley on 2009-08-10
I think it may be my modem blocking it and not my router. I'm going to try and put my modem on bridge mode when I get home tonight, maybe that will fix my problem.

---

### Post by ridgeland on 2009-08-10
I forgot about that.  My Mom had AT&T without a router just a modem and port 22 could not get through.  AT&T had customized the modem.  She later switched to Charter Cable and things were fine.  Later adding a router things were still fine, once it was set up.

---

### Post by jtholb on 2009-08-29
Any word on the outcome?  I've been having similar difficulties and am wondering if you ever found a solution.

---

