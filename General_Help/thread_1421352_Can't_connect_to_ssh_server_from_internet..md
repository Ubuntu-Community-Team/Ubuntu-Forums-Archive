---
title: "Can't connect to ssh server from internet."
date: 2010-03-04
forum: General Help
---

### Post by mahela007 on 2010-03-04
The ssh server I have at home is accessible from other computers on the LAN. However, on if I try to connect to it from another computer outside the LAN, I get a publickey error saying 'permission denied'.
What's wrong? 
I use key based logins. 
I have set up port forwarding on my router and the funny thing is that the current configuration worked just once.
Here is the output of ssh -v 
```
foobar@IBM-Ubuntu:~$ ssh -v <ip address of server>
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to <ip address of server> [<ip address of server>] port 22.
debug1: Connection established.
debug1: identity file /home/foobar/.ssh/identity type -1
debug1: identity file /home/foobar/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/foobar/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '<ip address of server>' is known and matches the RSA host key.
debug1: Found key in /home/foobar/.ssh/known_hosts:6
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/foobar/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/foobar/.ssh/identity
debug1: Trying private key: /home/foobar/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).
```
I've replaced the IP adress of my server with <ip address of server> and my Ubuntu username with 'foobar' for security.

---

### Post by richardjh on 2010-03-04
The error you are getting is related to the pass phrase for your key. 
Are you sure you have set up the keys correctly? 

I would suggest copying the known good key from a PC you know you can connect from to the machine that you cannot connect from and try again.

I do not think this is a networking / port forwarding / firewall problem.

Your edit shows that the id_rsa key was refused. That confirms my suspicions.

---

### Post by mahela007 on 2010-03-04
I'll try recopying the key. By the way, it's not accessible even from my LAN now..
Um. just to check if I have this right.. the publik key (in the id_rsa.pub file on the client) should be copied to the 'authorized keys' file on the server. (should this file be called 'Authorized_keys" or "Authorized_keys2"?)

---

### Post by richardjh on 2010-03-04
When you create you keypair the id_rsa.pub goes on the server (the machine running sshd) You save it in ~/.ssh/ as authorized_keys.
The name is specified in /etc/ssh/sshd_config on the server.

You use the id_rsa key on the client and save it in ~/.ssh/id_rsa on the client

You should specify a pass phrase when you created this key that you will need to type again to "unlock" the key to use it for authenticating against the server.

Permissions are important and files should be owned by you and be 400.

Once you have set this up a few times, it appears very easy to do, but I know how complicated it feels the first few times you do it.

---

### Post by mahela007 on 2010-03-04
Thanks a lot.. it seems that there has been a mismatch in the names. My config file points to authorized_keys while my actual file is called authorized_keys2. I'll try correcting this and post back

---

### Post by mahela007 on 2010-03-04
Nope.. still doesnt' work. Is it the key files that should have 400 permissions?
EDIT: I changed the permissions of all involved files to 400 and still nothing. I just noticed that I has rsa keys and that the ssh -v showed stuff about dsa keys. Do you think that's the problem?

EDIT : (yes that's the second EDIT ;-)) When ever I include my username on the server (like foobar@192.168.1.4) it works. However, if I just do "ssh 192.168.1.4" it doesn't work. I get the public key error.

---

### Post by richardjh on 2010-03-04
The id_rsa key on the client.

---

### Post by mahela007 on 2010-03-04
nope.. didn't work. :-( Please read the second EDIT in my previous post.. I wrote it after you posted. What should the permission for the other files in the .ssh folder on the client be?

---

### Post by richardjh on 2010-03-04
EDIT : (yes that's the second EDIT :wink:) When ever I include my username on the server (like foobar@192.168.1.4) it works. However, if I just do "ssh 192.168.1.4" it doesn't work. I get the public key error.

Is your username the same on both machines? That could be your problem.
You succeed to log in using ssh foobar@192.168.1.4 then the keys work.
You fail to log in using ssh 192.168.1.4, this suggests a user name problem.

---

### Post by mahela007 on 2010-03-04
Youre right.. I do have different usernames. Thanks a lot! However, I have one more question. I have set up a dyndns account for my ssh server. I can't connect to my ssh server if I provide the ssh client with my dyndns domain name. For example, if I do 'ssh [email]foobar@myserver.dyndyns.org[/email]" I get a connection refused error. Any ideas on what the problem here could be? 
PS You've really been a great help. Thanks a lot!

---

### Post by richardjh on 2010-03-04
OK. Glad that's sorted.

You can define the user name "foobar" in a new file on the client machine to make your connection easier

Create a file ~/.ssh/config

Put something like this in it to allow you to connect to your server on IP 192.168.1.4 as user "foobar" using the command

```
$ ssh HomePC
```
```
Host HomePC
  Hostname     192.168.1.4
  User         foobar
```As far as the DNS side goes, I would suggest posting that in a new thread.

---

### Post by mahela007 on 2010-03-04
the DYnDNS connection is working. When I enter my dyndns name I can connect to my routers settings page. This is why I believe that this is an SSH related problem.

---

### Post by richardjh on 2010-03-04
Can you check the port is open and you can connect to the server?

Try 
```
 telnet myserver.dyndns.org 22
```You should see something like this

```
Escape character is '^]'.
SSH-1.99-OpenSSH_3.6.1p2
```That will show if the problem is in the remote connection or actually on the server.

---

### Post by mahela007 on 2010-03-04
I used this tool to check if my port is open; Turns out that it is open
[http://www.dyndns.com/support/tools/openport.html](http://www.dyndns.com/support/tools/openport.html)

---

### Post by mahela007 on 2010-03-04
Well well well, it suddenly decided to work. So the only changes I made were to the name of the authorized_keys file and some file permissions. Thanks for your help..

---

### Post by richardjh on 2010-03-04
Phew. Got there in the end. I'm gonna stop watching this thread now.

---

### Post by mahela007 on 2010-03-04
yeah... phew. ;-)

---

