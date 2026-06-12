---
title: "SSH Hangs"
date: 2011-12-09
forum: General Help
---

### Post by spartan21 on 2011-12-09
I am trying to ssh (using a Mac) to a machine running Ubuntu 10.04.  The Ubuntu machine is connected via ethernet to the internet, while my Mac is wireless.  I have been successful in using vnc (Chicken of the VNC), but ssh hangs when I run the following command:

ssh -p 5900 -vvv [email]jeff@141.xxx.xx.xx[/email]

the debug information is as follows:

OpenSSH_5.6p1, OpenSSL 0.9.8r 8 Feb 2011
debug1: Reading configuration data /etc/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 141.xxx.xx.xx [141.xxx.xx.xx] port 5900.
debug1: Connection established.
debug1: identity file /Users/xxxx/.ssh/id_rsa type -1
debug1: identity file /Users/xxxx/.ssh/id_rsa-cert type -1
debug1: identity file /Users/xxxx/.ssh/id_dsa type -1
debug1: identity file /Users/xxxx/.ssh/id_dsa-cert type -1
debug1: ssh_exchange_identification: RFB 003.007


Evidently, ssh establishes a connection, but the process hangs on "ssh_exchange_identification."  And when I try to use the standard port 22 I get a "connection refused" error.

I haven't been able to find anything helpful online about this, so does anyone have any ideas?

Thanks for your help!

---

### Post by spartan21 on 2011-12-09
Problem solved, I needed openssh on the Ubuntu machine.  Once installed, ssh worked immediately.

Install using

```
sudo apt-get install openssh-server
```

---

