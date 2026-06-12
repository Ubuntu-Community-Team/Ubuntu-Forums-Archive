---
title: "Problem using trickle with ssh"
date: 2009-10-10
forum: General Help
---

### Post by delcypher on 2009-10-10
Hi I downloaded Trickle today (command-line standalone & daemon bandwidth controller). 

I can get it to work with wget e.g.

```
trickle -d 50 -s  wget http://www.google.co.uk/
```

But if I try and use it with SSH this happens

```
dan@dan-desktop:~$ trickle -d 30 -s ssh -v my-server.com
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to my-server.com [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/dan/.ssh/identity type -1
debug1: identity file /home/dan/.ssh/id_rsa type -1
debug1: identity file /home/dan/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3
debug1: match: OpenSSH_4.3 pat OpenSSH_4*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Resource temporarily unavailable

```

I found that if I changed the -d 50 to -d 60 then ssh usually works.

What's going on? I found that if I changed -d 50 to -d 51 that it often started working. Does SSH or sshd (on remote server) have some sort of minimum bandwidth threshold or something?

---

