---
title: "Access Remote Server &quot;FROM&quot; Ubuntu"
date: 2011-03-09
forum: General Help
---

### Post by pdubois on 2011-03-09
Dear Sirs, 

I tried to access a server 'foo.host.jp', usually in my other linux desktop
I have no problem accessing it with this command:

```
$ ssh pdubois@foo.host.jp
```it will simply prompt me with a password, then done.

But currently with my Ubuntu desktop I have problem.
It gives me this message. How can I resolve it?

```
$ ssh -v  pdubois@foo.host.jp
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /home/pdubois/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to foo.host.jp [201.175.151.54] port 22.
debug1: Connection established.
debug1: identity file /home/pdubois/.ssh/identity type -1
debug1: identity file /home/pdubois/.ssh/id_rsa type 1
debug1: identity file /home/pdubois/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.5
debug1: match: OpenSSH_5.5 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
Host key verification failed.
```

---

### Post by aeiah on 2011-03-09
have you tried clearing ~/.ssh/known_hosts ?

---

### Post by pdubois on 2011-03-09
> **aeiah said:**
> have you tried clearing ~/.ssh/known_hosts ?

You mean deleting the file "~/.ssh/known_hosts" in my ubuntu?

---

### Post by SeijiSensei on 2011-03-09
You're likely not using the identical private/public key pair on both machines. 

Copy the entire directory /home/username/.ssh (note the leading period; it's a "hidden" directory) from the machine that works into the same location on the machine that fails.  You should be able to connect.

The other alternative is to add the public key on the machine that fails to the remote's /home/user/.ssh/authorized_users file.  

See: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

