---
title: "Samba and XP"
date: 2010-02-16
forum: General Help
---

### Post by Rulesy on 2010-02-16
ARGH! Can somebody please help me set up SAMBA on 8.04.3 server? I've been at it for literally hours!

Here is my smb.conf file:

```
[global]
workgroup = WORKGROUP
server string = %h server (Samba, Ubuntu)
dns proxy = no
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d

security = user
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
invalid users = root

passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
socket options = TCP_NODELAY
wins support = no
wins server = Workgroup

[share]
browseable = yes
path = /var/www

```My server name is "ubuntu", if I try \\ubuntu\share in XP it says "Windows cannot find ' \\ubuntu\share'....." :(

All I want is a very simple setup to share my www folder over my private network, really not worried about security as there's only me on it!

Am I missing some steps here?

TIA

---

### Post by SteveHillier on 2010-02-16
I do not have my ubuntu machine with me at the moment but there are a few things I would ask you to check first.  Please don't shoot me if you have already done these.

Are the machines on the same network?  ie IP addresses in the same range (192.168.0.x for example)
Can you ping each machine from the other or are firewalls getting in the way?
Are you connecting though a switch or a router?
Can you see the windows machine from the ubuntu machine? (I use the 'network' option and use a samba share to see windows folders).
Is your Windows machine in the 'workgroup' workgroup.  Remember XP Home sets the workgroup to MSHOME and not WORKGROUP.

---

### Post by Rulesy on 2010-02-16
Ah no they are not in the same subnet, was using NAT instead of Bridged in VMware... have changed that now but I'm having new issues, will have to come back to this once that's resolved. Thanks for reply!

---

