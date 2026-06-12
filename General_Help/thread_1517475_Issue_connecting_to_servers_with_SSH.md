---
title: "Issue connecting to servers with SSH"
date: 2010-06-25
forum: General Help
---

### Post by arvsr1988 on 2010-06-25
Hey I'm having a problem connecting to servers through ssh. Heres's the output of my screen..

arvind@arvind-laptop:~$ ssh -vv [email]z4stagin@z4stagin.z4.aldenhosting.com[/email]
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to z4stagin.z4.aldenhosting.com [216.206.35.251] port 22.
debug1: Connection established.
debug1: identity file /home/arvind/.ssh/identity type -1
debug1: identity file /home/arvind/.ssh/id_rsa type -1
debug1: identity file /home/arvind/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host

Quick help would be appreciated..

---

### Post by anglican on 2010-06-25
> **arvsr1988 said:**
> Hey I'm having a problem connecting to servers through ssh. Heres's the output of my screen..

...

ssh_exchange_identification: Connection closed by remote host
...

The problem lies at your remote host... somewhere. It could be one of a number of things: firewall, sshd setup, hosts.allow...

The logs on the remote host should show you why it's refusing to connect.

H

---

### Post by arvsr1988 on 2010-06-25
Hey, 

I don't know if it is a problem with the remote host because i'm not able to connect to another server too. Also my friends and colleagues are able to connect to the server.  Please help.

Regards,
Arvind Sridharan

---

### Post by CharlesA on 2010-06-25
Have you set the server to use keys?

---

