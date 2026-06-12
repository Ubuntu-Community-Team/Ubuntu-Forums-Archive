---
title: "Scan outgoing ports"
date: 2011-01-20
forum: General Help
---

### Post by neon401 on 2011-01-20
Hi

I am attending a school with a very strict Websense filter to the extent that it actually prevents me from optimal study. Because of that, I'd like to bypass the filter using an SSH tunnel. The problem is, port 22 (and every other port I've tried, 80, 443 and various others) is blocked from outgoing traffic.

What I'm wondering is if there's any utility for scanning for open outgoing ports?

Thanks in advance


SSH debug:

```
oscar@oscar-laptop:~$ ssh -vvv -p 443 mc.nalum.no
OpenSSH_5.5p1 Debian-4ubuntu4, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to mc.nalum.no [81.167.60.146] port 443.
debug1: Connection established.
debug1: identity file /home/oscar/.ssh/id_rsa type -1
debug1: identity file /home/oscar/.ssh/id_rsa-cert type -1
debug1: identity file /home/oscar/.ssh/id_dsa type -1
debug1: identity file /home/oscar/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.5p1 Debian-4ubuntu4
debug1: match: OpenSSH_5.5p1 Debian-4ubuntu4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu4
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer

```

---

### Post by howefield on 2011-01-20
Please take it up with your school IT administrators. 

Thread closed.

---

### Post by overdrank on 2011-01-20
Hi and bypassing school restrictions are not supported on the forums. Thread closed.

---

