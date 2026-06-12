---
title: "SSH problems (ssh_exchange_identification: read: Connection reset by peer)"
date: 2012-05-08
forum: General Help
---

### Post by luckenbach on 2012-05-08
Hey, 

I was running 11.10 and decided to do the full upgrade and come up to 12.04 after the update SSH (not SSHD) is now misbehaving when attempting to connect to other OpenSSH instances. I say OpenSSH as I am running a DropBear sshd on my router and I am able to connect to it.


When attempting to connect to an OpenSSH server

```
[email]risk@skynet:~/.ssh[/email]$ ssh -vvv risk@someserver
OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /home/risk/.ssh/config
debug3: key names ok: [ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa,ssh-dss]
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to someserver [someserver] port 22.
debug1: Connection established.
debug1: identity file /home/risk/.ssh/id_rsa type -1
debug1: identity file /home/risk/.ssh/id_rsa-cert type -1
debug1: identity file /home/risk/.ssh/id_dsa type -1
debug1: identity file /home/risk/.ssh/id_dsa-cert type -1
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/risk/.ssh/id_ecdsa" as a RSA1 public key
debug1: identity file /home/risk/.ssh/id_ecdsa type 3
debug1: Checking blacklist file /usr/share/ssh/blacklist.ECDSA-521
debug1: Checking blacklist file /etc/ssh/blacklist.ECDSA-521
debug1: identity file /home/risk/.ssh/id_ecdsa-cert type -1
**ssh_exchange_identification: read: Connection reset by peer**
[email]risk@skynet:~/.ssh[/email]$
```


DropBear instance
```
risk@skynet:~/.ssh$ ssh -vvv root@darkness
OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /home/risk/.ssh/config
debug3: key names ok: [ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa,ssh-dss]
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to darkness [192.168.1.1] port 22.
debug1: Connection established.
debug1: identity file /home/risk/.ssh/id_rsa type -1
debug1: identity file /home/risk/.ssh/id_rsa-cert type -1
debug1: identity file /home/risk/.ssh/id_dsa type -1
debug1: identity file /home/risk/.ssh/id_dsa-cert type -1
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/risk/.ssh/id_ecdsa" as a RSA1 public key
debug1: identity file /home/risk/.ssh/id_ecdsa type 3
debug1: Checking blacklist file /usr/share/ssh/blacklist.ECDSA-521
debug1: Checking blacklist file /etc/ssh/blacklist.ECDSA-521
debug1: identity file /home/risk/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version dropbear_0.52
debug1: no match: dropbear_0.52
...

```

I have googled and ran most ALL fixes recommend both from the Debian and Arch sides and none of them seem to resolve my issue. Any ideas?

---

### Post by luckenbach on 2012-05-09
.... Looks like network abnormalities might be the culprit;

---

