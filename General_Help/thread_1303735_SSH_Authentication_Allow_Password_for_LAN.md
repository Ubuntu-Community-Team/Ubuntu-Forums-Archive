---
title: "SSH Authentication: Allow Password for LAN"
date: 2009-10-28
forum: General Help
---

### Post by zzzBrett on 2009-10-28
Is it possible to allow SSH authentication by password only when on the local network, but require a key when connecting from a remote network (internet)?

(OpenSSH)

---

### Post by zzzBrett on 2009-10-28
Any suggestions?

---

### Post by fluffman86 on 2009-10-28
If your computer is connected to the outside world at all, and you require a key there, why not just add your private key to the machines on your own lan?

---

### Post by zzzBrett on 2009-10-29
I could do that, but would rather find a way to use password authentication.

---

### Post by Lars Noodén on 2009-10-29
> **zzzBrett said:**
> Is it possible to allow SSH authentication by password only when on the local network, but require a key when connecting from a remote network (internet)?

(OpenSSH)

Look at Match in [sshd_config](http://manpages.ubuntu.com/manpages/karmic/en/man5/sshd_config.5.html).  It allows you to change the value of PasswordAuthentication based on group or network.  Substitute your subnet for the one below.


```

# require a key for everybody
PasswordAuthentication no

# any member of the group 'downstairs' can log in without a key
# while connecting from the subnet 
Match Address 192.168.0.0/16 Group downstairs
    PasswordAuthentication yes

```

Match also allows the following to be changed: AllowTcpForwarding, Banner, ChrootDirectory, ForceCommand, GatewayPorts, GSSAPIAuthentication, HostbasedAuthentication, KbdInteractiveAuthentication, KerberosAuthentication, MaxAuthTries, MaxSessions, PermitOpen, PermitRootLogin, RhostsRSAAuthentication, RSAAuthentication, X11DisplayOffset, X11Forwarding, and X11UseLocalHost.

---

### Post by zzzBrett on 2009-10-29
Exactly what I was looking for. Thanks.

---

### Post by plugwash on 2012-11-06
> **Lars Noodén said:**
> 
```

# require a key for everybody
PasswordAuthentication no

# any member of the group 'downstairs' can log in without a key
# while connecting from the subnet 
Match Address 192.168.0.0/16 Group downstairs
    PasswordAuthentication yes

```

Just to clarify this example requires them to be on the subnet AND in the group. If you just want to require them to be on the subnet then leave out the Group clause.

---

### Post by wildmanne39 on 2012-11-06
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

