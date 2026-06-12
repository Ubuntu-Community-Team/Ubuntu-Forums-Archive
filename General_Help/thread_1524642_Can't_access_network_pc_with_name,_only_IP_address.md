---
title: "Can't access network pc with name, only IP address.."
date: 2010-07-05
forum: General Help
---

### Post by r2rX on 2010-07-05
Hi guys,

I'm using Ubuntu 10.04 x64. All Samba-related software is installed and configured.

Now, there are several PC's on the network. All of the machines (including my own) have NTFS partitions shared.

My machine is the only one with Linux on it, the rest are Windows 7. The Windows machines can access my share either by my 'Name' (i.e. //rx) and my IP address.

For some reason, however, I can only access their machines via their IP address...not their name.

We have specified IP addresses manually, so no DHCP involved. And the Windows machines are using ESET Smart Security.

If there's any other info you'd require, i'll gladly provide.

r2rX  :D

---

### Post by theozzlives on 2010-07-05
Edit the /etc/hosts file to look something like the following:
```
127.0.0.1	localhost

127.0.0.1   ozzie-laptop.ipserver.com   ozzie-laptop
192.168.1.4     ozzie-laptop
192.168.1.6     www-server
192.168.1.3     windows-7
```

That should take care of it, of course change the IPs and Names to match your network.

---

### Post by r2rX on 2010-07-05
Dude, I could kiss you. :)

I love you guys. :) From day one, since starting with Linux (specifically Ubuntu) I have had nothing but amazing assistance.

.....lots of love, guys. ;)

r2rX  :D

---

