---
title: "ubuntu 9.10 terminal TCPKeepAlive"
date: 2010-02-24
forum: General Help
---

### Post by unix_user on 2010-02-24
I ssh to home server Ubuntu 9.10 from external location using putty
and would like to remain connected until I close. I noticed it
disconnects after a period of inactivity.

This server is registered with dyndns and gets its IP changed sometimes.
It uses ddclient to get updated IP.

I have checked /etc/ssh/sshd_config and it has following
[FONT=Courier New]TCPKeepAlive yes[/FONT]

Is there any setting needed to avoid losing connection.

Thanks for assistance

---

