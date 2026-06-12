---
title: "Debuging SSH connection with public key"
date: 2010-11-09
forum: General Help
---

### Post by ryanfx on 2010-11-09
Hello all,

I am trying to debug a problem where I can't connect to a remote SSH server.  I do not have admin rights on the box, however I have a valid account and can login fine with a password, I just wanted to use my public key instead.

I copied over my ~/.ssh/id_rsa.pub to the remote server to ~/.ssh/authorized_keys.  I tried to connect to the server but it is not allowing me to authenticate when I ask it to use public keys instead of passwords.  Any ideas?

```

ryan@TehLaptop:~$ ssh -v -o PreferredAuthentications=publickey ryan@unix.xxxxxxx.xxx
OpenSSH_5.5p1 Debian-4ubuntu4, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to unix.xxxxx.xxx [xxx.xxx.xxx.xxx] port 22.
debug1: Connection established.
debug1: identity file /home/ryan/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/ryan/.ssh/id_rsa-cert type -1
debug1: identity file /home/ryan/.ssh/id_dsa type -1
debug1: identity file /home/ryan/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3
debug1: match: OpenSSH_4.3 pat OpenSSH_4*
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
debug1: Host 'unix.xxxxxxxx.xxx' is known and matches the RSA host key.
debug1: Found key in /home/ryan/.ssh/known_hosts:3
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/ryan/.ssh/id_rsa
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: Trying private key: /home/ryan/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey,gssapi-with-mic,password).

```

---

### Post by CharlesA on 2010-11-09
Is there anything in ~/.ssh/ ?

I usually use ***ssh-copy-id*** to transfer keys to a remote server.

[http://linux.die.net/man/1/ssh-copy-id](http://linux.die.net/man/1/ssh-copy-id)

---

### Post by ryanfx on 2010-11-09
Yes.  On my local box:

```

ryan@TehLaptop:~/.ssh$ ls -l
total 20
-rw------- 1 ryan ryan 1743 2010-05-27 21:02 id_rsa
-rw-r--r-- 1 ryan ryan  396 2010-05-27 21:02 id_rsa.pub
-rw-r--r-- 1 ryan ryan 8840 2010-11-03 16:56 known_hosts

```

remote box:

```

[ryan@unix14 ~]$ 
[ryan@unix14 ~]$ ls -la
...
drwx------  2 ryan  wheel  2048 Nov  9 13:27 .ssh
...

```

```

[ryan@unix14 ~]$ ls -la ~/.ssh/authorized_keys 
-rw------- 1 ryan wheel 396 Nov  3 17:26 /afs/xxxxxxxx/usr15/ryan/.ssh/authorized_keys

```

---

### Post by CharlesA on 2010-11-09
Yeah.. I'd remove authorized_keys file on the remote machine and use ssh-copy-id to make sure they key is set correctly.

---

### Post by ryanfx on 2010-11-09
> **CharlesA said:**
> Yeah.. I'd remove authorized_keys file on the remote machine and use ssh-copy-id to make sure they key is set correctly.

I did that.  Didn't help.  I'll keep that utility in mind for the future though.

---

### Post by CharlesA on 2010-11-09
Can you post yer sshd_config file please.

Also, what kind of key are you using, dsa or rsa?

---

### Post by ryanfx on 2010-11-09
> **CharlesA said:**
> Can you post yer sshd_config file please.

Also, what kind of key are you using, dsa or rsa?

As I said in the first post, I don't have root access on the box so that config is not accessible, I am using RSA keys.

---

### Post by CharlesA on 2010-11-09
Unless you are chroot'd into yer home directory, the config file should be readable.

Change the group of .ssh to ryan:ryan and see if that'll let you connect.

Should look like this:

```
charles@atlantis:~$ ls -ld .ssh
drwx------ 2 charles charles 4096 2010-10-20 19:05 .ssh
charles@atlantis:~$ ls -l .ssh/
total 8
-rw------- 1 charles charles 386 2010-10-17 20:05 authorized_keys
-rw-r--r-- 1 charles charles 884 2010-10-20 19:05 known_hosts

```

---

### Post by efflandt on 2010-11-09
Your ~/.ssh should have 700 permission drwx------ (which it does) and everything in that directory should have 600 permission -rw------- (which is not the case yet on your local box).

efflandt@XPS-8100:~$ ls -al ~/.ssh
total 40
drwx------  2 efflandt efflandt 4096 2009-11-08 18:57 .
drwxr-xr-x 33 efflandt efflandt 4096 2010-11-09 12:28 ..
-rw-------  1 efflandt efflandt  831 2010-02-27 14:06 authorized_keys2
-rw-------  1 efflandt efflandt 1742 2009-10-26 02:01 config
-rw-------  1 efflandt efflandt  736 2004-06-07 10:21 id_dsa
-rw-------  1 efflandt efflandt  605 2004-06-07 10:21 id_dsa.pub
-rw-------  1 efflandt efflandt  545 2004-06-07 10:22 identity
-rw-------  1 efflandt efflandt  349 2004-06-07 10:22 identity.pub
-rw-------  1 efflandt efflandt 5746 2009-10-26 02:01 known_hosts

identity is my old rsa ssh1 key and id_dsa is my ssh2 key.  Both keys are in authorized_keys2.  Make sure that lines in your **authorized_keys** are NOT actually wordwrapped (each key should be on its own continuous long line).

ssh-dss AAAAB3Nza...secret_long_line...Q== efflandt@laptop
ssh-rsa AAAAB3Nza...secret_long_line...k= rsa-key-20060518

It does not matter that the dsa key shows efflandt@laptop, that was just the computer used to generate it (works from any client to any server).

---

