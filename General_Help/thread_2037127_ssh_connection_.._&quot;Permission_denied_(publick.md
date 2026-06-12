---
title: "ssh connection .. &quot;Permission denied (publickey)&quot;"
date: 2012-08-03
forum: General Help
---

### Post by dragonfly41 on 2012-08-03
I've created ssh keys as per the manual

sudo ssh-keygen -t rsa

RSA key pair (passphrase blank) was created in

/home/user/.ssh/id_rsa
/home/user/.ssh/id_rsa.pub

and I setup ~/.ssh/config and  /etc/ssh/ssh_config


I'm not able to connect to a phpcloud server via ssh

sudo sftp -vi IdentityFile=/home/user/.ssh/id_rsa \ [EMAIL="mycontainername@mycontainername.my.phpcloud.com"]mycontainername@mycontainername.my.phpcloud.com[/EMAIL]

I get error message "Permission denied (publickey)"

......

Here is the terminal output ..

Note 1 -  this output has been edited to refer to "mycontainername" as alias

Note 2 - why is my RSA key not found .. /home/user/.ssh/id_rsa not accessible: No such file or directory.   Permissions set to 600 .. user www-data

Note 3 - why is there reference to /root/.ssh for RSA key instead of /home/user/.ssh?

> 
$ sudo sftp -vi IdentityFile=/home/user/.ssh/id_rsa \ [EMAIL="mycontainer@mycontainer.my.phpcloud.com"]mycontainer@mycontainer.my.phpcloud.com[/EMAIL]
OpenSSH_5.5p1 Debian-4ubuntu6, OpenSSL 0.9.8o 01 Jun 2010
Warning: Identity file IdentityFile=/home/user/.ssh/id_rsa not accessible: No such file or directory.
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to mycontainer.my.phpcloud.com [50.16.113.111] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_rsa-cert type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: identity file /root/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu7-devpaas1
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu7-devpaas1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu6
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
The authenticity of host 'mycontainername.my.phpcloud.com (50.16.113.111)' can't be established.
RSA key fingerprint is 56:4c:10:cc:c9:3d:b3:9d:4d:6a:f1:c7:6b:03:65:35.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'mycontainername.my.phpcloud.com,50.16.113.111' (RSA) to the list of known hosts.
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/id_rsa
debug1: Trying private key: /root/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).
Couldn't read packet: Connection reset by peer



---

### Post by LewisTM on 2012-08-03
Erase the keys and try again without sudo anywhere. There is no need AFAIK.
Adding sudo means your are making keys for the root user, not yourself.

---

### Post by phrak on 2012-08-03
You did add your id_rsa.pub to the host machines authorized_keys file right?

---

### Post by dragonfly41 on 2012-08-03
Thanks for the tips

I started again .. not using sudo .. and regenerated RSA keys

no passphrase used

I uploaded the fresh public key to phpcloud

I copied id_rsa.pub into /home/user/.ssh/authorized_keys

This time there is no reference to /root/.ssh/

but I still get this at end of output ..

> 
<snip>
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/user/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/user/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).
Couldn't read packet: Connection reset by peer


---

### Post by dragonfly41 on 2012-08-03
Postscript ..

With this fresh set of RSA keys created (not at root) I've managed to make an SSH connection to phpcloud server (first time) using FileZilla after changing the format of id_rsa to PuTTy format.

But I still don't understand why the terminal command gives that error.

---

