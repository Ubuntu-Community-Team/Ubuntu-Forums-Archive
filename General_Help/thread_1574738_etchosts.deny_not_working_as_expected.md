---
title: "/etc/hosts.deny not working as expected"
date: 2010-09-14
forum: General Help
---

### Post by hwong557 on 2010-09-14
Hi,

I'm trying to secure my SSH using DenyHosts. They suggest testing to see if sshd supports tcp_wrappers: [http://denyhosts.sourceforge.net/ssh_config.html](http://denyhosts.sourceforge.net/ssh_config.html)

Unfortunately, with "sshd: 127.0.0.1" and "sshd: localhost" in the /etc/hosts.deny file, I am still able to access my ssh server from my own computer using "ssh localhost".  If I add "sshd: ALL" to the hosts.deny, then I get "ssh_exchange_identification: Connection closed by remote host" error. I'm running Maverick with the regular openssh-server installed from the repos. How do I make the hosts file do what it is supposed to do? Thanks!

EDIT: "ssh 127.0.0.1" does seems to be blocked...

---

### Post by Richard1979 on 2010-09-14
Allow rules are more important than Deny rules.

Try:

> sudo ufw status numbered

The lower numbers are more important.
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

To properly block an IP, add the following into /etc/ufw/before.rules
> -A ufw-before-input -s 111.222.333.444 -j DROP
Where 111.222.333.444 is the address you want to block.

Then:
> sudo ufw reload

And the IP will be blocked.

---

