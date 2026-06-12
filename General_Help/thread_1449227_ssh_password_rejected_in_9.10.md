---
title: "ssh password rejected in 9.10"
date: 2010-04-07
forum: General Help
---

### Post by jerome schatten on 2010-04-07
On the several machines on my network, I am having difficulty using ssh
and sftp.

Machines are as follows:

1. a Slack machine 2.4.26 kernel        

2. a Suse 10 machine 2.6.22.xxx kernel

3. a Ubuntu 9.10 machine 2.6.31.20.xxx kernel

I can use sftp/ssh between 1 and 2. in either direction - no problem.

I cannot sftp/ssh between 3 and anything. sshd is running on the ubuntu
machine. I used to be able to sftp/ssh between 2 and 3 but only if 2
started the process.

The failure is machine #3 not accepting the password to or from the other
machines,  or at least that's how it presents.

All machines can ping each other.

The configs are defaults

I only dimly understand what's going on. Can someone suggest how I might
fix this? 

Thanks,
jerome

---

### Post by cdenley on 2010-04-07
Need more information. What is the verbose output from your failed connection attempts (ssh -v user@server)? What user are you attempting to connect as?

Run these commands on the ubuntu server:
```

dpkg -l openssh-server
sudo netstat -tlnp
grep sshd /var/log/auth.log
grep "^[^#]" /etc/ssh/sshd_config

```

---

### Post by jerome schatten on 2010-04-07
Thanks... I'll try that to learn from your suggestion. 

The problem was mine in the making: I was trying to log into the root directory on the Ubuntu machine from the Slack machine. That is from Slack I sent: **ssh 192.168.0.100** to which Ubuntu denied the password. I looked in auth.log which gave me the clue. **ssh user-name@192.168.0.100** accepted the password fine. Silly me.
jerome

---

