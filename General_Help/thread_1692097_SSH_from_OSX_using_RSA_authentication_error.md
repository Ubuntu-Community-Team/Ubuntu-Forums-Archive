---
title: "SSH from OSX using RSA authentication error"
date: 2011-02-20
forum: General Help
---

### Post by guitarguy12387 on 2011-02-20
Hey guys,

First timer here, so be gentle with me haha!

Anyway, I am trying to set up remote login via SSH from my Mac to an Ubuntu desktop. Here is the error i am getting:
```
Permission denied (publickey,password).

```I'll give background:
- Both computers are on the same network
- I'm not using the default port 22
- I have successfully logged in using password authentication, so it isn't a firewall/iptables issue i don't think. I've already worked through those issues haha!
- I haven't set up any tcp wrappers on the server yet, so nothing is being denied
- I believe the server sshd_config file is setup correctly. I can post it if needed.

Here's debugging info:
```
bash-3.2$ ssh localuser@xxx.xxx.x.x -v
OpenSSH_5.2p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /etc/ssh_config
debug1: Connecting to xxx.xxx.x.x [xxx.xxx.x.x] port xx.
debug1: fd 3 clearing O_NONBLOCK
debug1: Connection established.
debug1: identity file /Users/localuser/.ssh/id_rsa type 1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '[xxx.xxx.x.x]:xx' is known and matches the RSA host key.
debug1: Found key in /Users/localuser/.ssh/known_hosts:12
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /Users/localhost/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: No more authentication methods to try.
Permission denied (publickey,password).

```It looks like it is working, then for some reason just quits?!

Here's client ssh_config file:
```
bash-3.2$ cat ssh_config
#    $OpenBSD: ssh_config,v 1.22 2006/05/29 12:56:33 dtucker Exp $

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

# Host *
#   ForwardAgent no
#   ForwardX11 no
#   RhostsRSAAuthentication no
   RSAAuthentication yes
   PasswordAuthentication no
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
   ConnectTimeout 500
   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
   Port xxxx
   Protocol 2
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no

```I have mostly just been playing around with the config file trying to see if i missed something.

Anyway, i'm not sure what to try now! Any advice would be much appreciated.

---

### Post by asmoore82 on 2011-02-20
You never mention that you have actually copied your public key over.

---

### Post by kb2001 on 2011-02-20
This is what I see in mine (this is Solaris to Solaris, different but the same), relevant parts included

```

debug1: Next authentication method: publickey
debug1: Trying private key: /home/myuser/.ssh/identity
debug1: Trying private key: /home/myuser/.ssh/id_rsa
debug1: read PEM private key done: type RSA
debug1: Authentication succeeded (publickey)
debug1: channel 0: new [client-session]
debug1: send channel open 0
debug1: Entering interactive session.
debug1: ssh_session2_setup: id 0

```

Do you have your private key on the Ubuntu machine?  It looks like you didn't get any response when it tried to use the keys, just carried on denying you, almost as if it is timing out or ignoring the client request to authenticate with keys.  Not sure how, since you have it set to 500 seconds

---

### Post by guitarguy12387 on 2011-02-21
> You never mention that you have actually copied your public key over.

Oops, sorry about that. Yes, i did copy my public key over.

> Do you have your private key on the Ubuntu machine?
No, the Ubuntu machine is acting as the server. So i generated the key pair on my osx (client) machine, stored the private key locally, and copied the public key to the Ubuntu machine. That is correct, yeah?

> It looks like you didn't get any response when it tried to use the keys,  just carried on denying you, almost as if it is timing out or ignoring  the client request to authenticate with keys.  Not sure how, since you  have it set to 500 seconds 	
Right, exactly. I have been trying to parse the config files, trying to see if there is something else i am missing, but can't find anything obvious.

---

### Post by asmoore82 on 2011-02-21
Just to clarify:
The private key should be on the client at "$HOME/.ssh/id_rsa"
The public key should be on the server at "$HOME/.ssh/authorized_keys"

The next logical troubleshooting step is to attempt to SSH
from the server *to itself* with keys:
```
***user@server*:~ $** ssh $HOSTNAME
```

---

### Post by asmoore82 on 2011-02-21
[SIZE="3"]*Got it!*[/SIZE]

I just tried this "logical troubleshooting step" on my own laptop &#8212;
and it wouldn't work! Really freaked me out for a few minutes.

Then I remembered that SSH demands good file ownership and permissions.
"$HOME" and "$HOME/.ssh" must not be *writable* by others,
"$HOME/.ssh/authorized_keys" must not be *readable or writable* by others.

I had opened up some write permissions on my "$HOME"
a while back and forgot to close it!

---

### Post by guitarguy12387 on 2011-02-21
> Just to clarify:
The private key should be on the client at "$HOME/.ssh/id_rsa"
The public key should be on the server at "$HOME/.ssh/authorized_keys"Yes, that is correct.

> [SIZE=3]*Got it!*[/SIZE]

I just tried this "logical troubleshooting step" on my own laptop &#8212;
and it wouldn't work! Really freaked me out for a few minutes.

Then I remembered that SSH demands good file ownership and permissions.
"$HOME" and "$HOME/.ssh" must not be *writable* by others,
"$HOME/.ssh/authorized_keys" must not be *readable or writable* by others.

I had opened up some write permissions on my "$HOME"
a while back and forgot to close it!     Haha sorry about that! But yeah, those folders have the appropriate permissions already:

```

localuser@ubuntu-desktop:~$ ls ~/.ssh -l
total 4
-rw------- 1 localuser localuser 414 2011-02-20 21:07 authorized_keys
localuser@ubuntu-desktop:~$ ls ~/.ssh/authorized_keys -l
-rw------- 1 localuser localuser 414 2011-02-20 21:07 ~/.ssh/authorized_keys

```

> 
The next logical troubleshooting step is to attempt to SSH
from the server *to itself* with keys:
 	Code:
 	***user@server*:~ $** ssh $HOSTNAME 

Ohh thanks ill give that a try!

---

### Post by aeiah on 2011-02-21
ssh is pretty rock solid. whenever it doesnt work for me its usually something silly ive done like:

[LIST]
[*]the client is using a different private key to the one i generated (if ive generated two)

[*]i copied over the private key, id_rsa instead of id_rsa.pub

[*]i have a malformed authorized_keys file (just do cat id_rsa.pub >> authorized_keys again)
[/LIST]

maybe increase your verbosity level (-vvv). my login is the same as yours (and works) but it just lets me in after ```
debug1: SSH2_MSG_SERVICE_ACCEPT received
```

---

### Post by guitarguy12387 on 2011-02-21
Hey, thanks for the tips!

This is my first time using public key auth, so it is the only key set i have. I used scp too, so there shouldn't be any copy pasting issues.

Anyway, i got it working! Haha. Not exactly sure why, but...

Since my last post, the things i changed are:
1) I hadn't realized, but i was still allowing password authentication on the server machine (i had only disabled it on the client machine). Not convinced that that should make a difference... but i changed it anyway.
2) I changed the file permissions according to exactly what is described in this tutorial:
[http://kimmo.suominen.com/docs/ssh/](http://kimmo.suominen.com/docs/ssh/)

---

