---
title: "How can I disable sshd for a certain time?"
date: 2010-02-19
forum: General Help
---

### Post by yu xintian on 2010-02-19
Hi ,all ! I have a computer running Ubuntu Server 9.10.I think some one is attacking it: they always try to log in to it via ssh. I think I need to disable ssh log in for a certain time if a person failed for 3 times(only disable that one, other people should be OK).There seems to be no that key words in "man sshd_config" .Does anybody have advice for this issue ? Thank you ! :)

---

### Post by d3v1150m471c on 2010-02-19
save the following as/in /etc/network/if-up.d/bfa_protection

```


#!/bin/bash
[ "${METHOD}" != loopback ] || exit 0
/sbin/iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
/sbin/iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 3 --rttl --name SSH -j DROP

```Then:
```

chmod u+x /etc/network/if-up.d/bfa_protection

```

---

### Post by ironclaw on 2010-02-19
> **yu xintian said:**
> Hi ,all ! I have a computer running Ubuntu Server 9.10.I think some one is attacking it: they always try to log in to it via ssh. I think I need to disable ssh log in for a certain time if a person failed for 3 times(only disable that one, other people should be OK).There seems to be no that key words in "man sshd_config" .Does anybody have advice for this issue ? Thank you ! :)
You can also have a look at [DenyHosts]("http://denyhosts.sourceforge.net/"), which is designed for this exact purpose.

---

### Post by tgalati4 on 2010-02-19
fail2ban

---

### Post by Primefalcon on 2010-02-19
You don't need to do that, just install firestarter (it's a graphical front end for your systems firewall)

```
sudo apt-get install firestarter
```

and remove permissions for port 22

firestarter will also show you any attempts that have been made to access your system that have been denied, so you'll be able to see the IP address in question

---

### Post by Johnny B on 2010-02-19
I use denyhosts, its in the repos and does exactly what you're asking for.

---

### Post by GolemXIV on 2010-02-19
You really should dissable password logins and just use public key authorization.

This link will guide you through setting up public key authorization
[http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)

Then just disable password authentication in /etc/ssh/sshd_config
Then finally restart the daemon with "sudo /etc/init.d/ssh restart" and enjoy

---

### Post by Neezer on 2010-02-19
As golem said, I would recommend using an RSA key to login instead of a password. Also, fail2ban works great.

---

### Post by 2hot6ft2 on 2010-02-20
I used this guide when it came to the RSA keys.
[http://help.ubuntu.com/community/SSH/OpenSSH/Keys](http://help.ubuntu.com/community/SSH/OpenSSH/Keys)

But since this is a server you're talking about and not a home user ssh setup then fail2ban is the way to go, it can blacklist them for a period of time that you set after a # of failed attempts within a time frame that you set.

---

### Post by yu xintian on 2010-02-20
Well,thank you for your advice! You help me a lot ! :D

---

### Post by yu xintian on 2010-02-22
> **2hot6ft2 said:**
> I used this guide when it came to the RSA keys.
[http://help.ubuntu.com/community/SSH/OpenSSH/Keys](http://help.ubuntu.com/community/SSH/OpenSSH/Keys)

But since this is a server you're talking about and not a home user ssh setup then fail2ban is the way to go, it can blacklist them for a period of time that you set after a # of failed attempts within a time frame that you set.

Hi,2hot6ft2 ! Tank you for your help !:)  Can I do it in firewall? My friend told me there should be a way to do it,but either of us know how to do.:confused:

---

### Post by yu xintian on 2010-02-22
> **d3v1150m471c said:**
> save the following as/in /etc/network/if-up.d/bfa_protection

```


#!/bin/bash
[ "${METHOD}" != loopback ] || exit 0
/sbin/iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
/sbin/iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 3 --rttl --name SSH -j DROP

```Then:
```

chmod u+x /etc/network/if-up.d/bfa_protection

```


Hi,Devil ! Thank you for your script. But it works in my friend's computer ( Ubuntu server edition 9.10 -32 bit) ,does not work in my computer(Ubuntu server edition 9.10 -64 bit).We did it in the same way.

---

### Post by gmargo on 2010-02-22
I recommend not using port 22.  Script kiddies the world over are constantly hammering on it.  Pick a non-standard port and suddenly you won't see all that traffic in the log.  If you're using an external firewall/router device you can probably configure it to forward port XYZ to port 22 on your system.

---

