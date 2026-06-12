---
title: "Ssh denies login"
date: 2011-01-11
forum: General Help
---

### Post by Mr.Kappa on 2011-01-11
Hi everybody! I run a small ubuntu server, lately i was messing up with user groups to give some users on the local network the possibility to work with samba. When i logged out from ssh, i could not get it to let me loggon again. I noticed that my user, which i thought i didn't touch (i thought :( ) had lost all the groups it was in (also the admin group). I readded the admin group to my user but i still cannot login from ssh.
Can someone suggest how can i fix this?? i haven't tried other things because the server actually is in a freezing garage 30 km from me, so i prefer not stay there a lot of time :P



ps the ssh verbose output seems normal.. after three tries it just tells me ```
debug1: Authentications that can continue: publickey,password
debug1: No more authentication methods to try.
Permission denied (publickey,password).
 
``````
OpenSSH_5.5p1 Debian-4ubuntu4, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to matteserver.no-ip.org [87.9.115.131] port 22.
debug1: Connection established.
debug1: identity file /home/roberto/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/roberto/.ssh/id_rsa-cert type -1
debug1: identity file /home/roberto/.ssh/id_dsa type -1
debug1: identity file /home/roberto/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.5p1 Debian-4ubuntu4
debug1: match: OpenSSH_5.5p1 Debian-4ubuntu4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'matteserver.no-ip.org' is known and matches the RSA host key.
debug1: Found key in /home/roberto/.ssh/known_hosts:1
Warning: Permanently added the RSA host key for IP address '87.9.115.131' to the list of known hosts.
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/roberto/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/roberto/.ssh/id_dsa
debug1: Next authentication method: password

```

---

### Post by Mr.Kappa on 2011-01-12
I tried purging ssh and reinstalling but nothing changed... anybody?

---

### Post by Mr.Kappa on 2011-01-14
Solved this using usermod -G command to restore my user from the recovery console and purging/reinstalling openssh-server.

---

### Post by Mr.Kappa on 2011-01-14
Solved this using usermod -G command to restore my user from the recovery console and purging/reinstalling openssh-server.

---

