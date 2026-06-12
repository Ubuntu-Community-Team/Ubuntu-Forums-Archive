---
title: "SSH Isolation"
date: 2010-08-26
forum: General Help
---

### Post by sshwoes on 2010-08-26
I have an eerie situation here.

I use an XP machine at work and rely on PuTTY to SSH around. I have the ability to SSH into most of the machines I have access to, except for my desktop at home. However, I can SSH into my desktop at home from anywhere else (including my cell phone).

When trying to connect via PuTTY, it just sits until I get a "Connection Timed Out" error. Currently I'm just using one of the other machines as a middle man between work and home, but I would love to figure out the problem. (I'm also using Hamachi to get access to my desktop's SMB share and it is having similar problems.) Anyway.

I added

```
iptables -A INPUT -p TCP --source my.work.computer.ip -j LOG
```

And the following shows up when I try to SSH from work:

```
Aug 26 16:35:02 home-hostname kernel: [1029246.080477] IN=eth0 OUT= MAC=eth0:mac:address SRC=my.work.computer.ip DST=192.168.1.199 LEN=48 TOS=0x00 PREC=0x20 TTL=116 ID=64819 DF PROTO=TCP SPT=1102 DPT=22 WINDOW=65535 RES=0x00 SYN URGP=0
```

So I know they can communicate at some level. The SSH server install is completely default and iptables is mostly off (it's behind a router). It's frustrating because I *know* it's possible to connect to this computer from elsewhere, and I *know* that I can connect to other computers, it seems to just fail in between these specific machines.

Any ideas?

EDIT: Well, I suppose this is relevant. The home desktop was an Ubuntu 9.04 installation that was upgraded to a 10.04 with the Update Manager. This is the first time I've ever upgrade Ubuntu versions without a complete reinstall.

---

