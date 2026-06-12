---
title: "How to use public-key ssh authentication"
date: 2012-03-26
forum: General Help
---

### Post by Poma on 2012-03-26
I have 2 ubuntu 12.04 (beta) servers (node1 and node2) and want to establish passwordless root access between them. Other users should not have passwordless access. Also note that ssh default port is changed to 220.

Here's what I did:
```
sudo -i
cd /root/.ssh
ssh-keygen -t rsa # with default name and empty password
cat id_rsa.pub > authorized_keys
```

then copied id_rsa & id_rsa.pub to node2 and added id_rsa.pub to authorized_keys. Both hosts have the same /root/.ssh/config file:
```
Host node1
Hostname 1.2.3.4
Port 220
IdentityFile /root/.ssh/id_rsa

Host node2
Hostname 5.6.7.8
Port 220
IdentityFile /root/.ssh/id_rsa
```

Now the problem is that when I type "ssh node2" it asks me for password. What may be the problem?

Debug info:
```
debug1: Server host key: RSA ***
debug1: Host '[*.*.*.*]:220' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:6
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /root/.ssh/id_rsa ((nil))
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/id_rsa
debug1: read PEM private key done: type RSA
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
```

Permissions:
```
drwx------ 2 root root   4096 Mar 26 15:34 .ssh

-rw------- 1 root root  840 Mar 26 14:50 authorized_keys
-rw-r--r-- 1 root root  225 Mar 26 15:34 config
-rw------- 1 root root 1679 Mar 26 14:47 id_rsa
-rw-r--r-- 1 root root 2652 Mar 26 14:39 known_hosts
```

Some lines from config files:
```
PermitRootLogin without-password
RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile  %h/.ssh/authorized_keys
UsePAM no # also tried yes
```

---

### Post by gsgleason on 2012-03-26
You might try running the sshd server in debug mode to see if it sheds any more light on the situation.

---

### Post by Poma on 2012-03-26
Here's the result

```
debug1: userauth-request for user root service ssh-connection method none [preauth]
debug1: attempt 0 failures 0 [preauth]
debug1: PAM: initializing for "root"
debug1: PAM: setting PAM_RHOST to "*.*.*.*"
debug1: PAM: setting PAM_TTY to "ssh"
debug1: userauth-request for user root service ssh-connection method publickey [preauth]
debug1: attempt 1 failures 0 [preauth]
debug1: test whether pkalg/pkblob are acceptable [preauth]
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: temporarily_use_uid: 0/0 (e=0/0)
debug1: trying public key file /root/.ssh/authorized_keys
debug1: fd 4 clearing O_NONBLOCK
debug1: matching key found: file /root/.ssh/authorized_keys, line 2
Found matching RSA key: ****
debug1: restore_uid: 0/0
debug3: mm_answer_keyallowed: key 0x7f0647b0c1b0 is allowed
debug3: mm_request_send entering: type 22
debug2: userauth_pubkey: authenticated 0 pkalg ssh-rsa [preauth]
Postponed publickey for root from *.*.*.* port 38887 ssh2 [preauth]
```

---

### Post by gsgleason on 2012-03-26
More debug flags?

I searched for the 'postponed' message and got some results: [http://www.linuxquestions.org/questions/linux-software-2/ssh-public-key-authentication-problem-373023/](http://www.linuxquestions.org/questions/linux-software-2/ssh-public-key-authentication-problem-373023/)

Check /var/log/messages and /var/log/secure for stuff.

---

### Post by asmoore82 on 2012-03-26
SSH is understandably picky about file permissions, for passwordless auth to work, the "$HOME/.ssh" folder and sensitive files must have absolutely no permissions for other users, not even read only.

try: ```
chmod 700 "$HOME/.ssh"
chmod 600 "$HOME/.ssh/authorized_keys"
chmod 600 "$HOME/.ssh/id_rsa
``` on both boxes.

---

### Post by Poma on 2012-03-27
As you can see I've already set permissions exactly like you said

---

### Post by azmyth on 2012-03-27
Did you set "PasswordAuthentication no" in the sshd_config file? Also, if you have a key password set it will ask you for this.

---

### Post by bubylou on 2012-03-27
I believe your suppose to use the id_rsa key for both the server authorized_keys file and the client. Not the id_rsa.pub. I also advice not allowing signing in as root over ssh. You should instead sign in as a user who can use sudo. Even with key authentication it would still be a nice security addition.

---

### Post by Poma on 2012-03-27
Updated my previous answer with more debug lines (only the last ones that are relevant). Also I don't have log files that you wanted but here is some interesting stuff from /var/log/auth:
```
Mar 27 11:50:05 node2 sshd[24111]: debug1: sshd version OpenSSH_5.9p1 Debian-4ubuntu1
Mar 27 11:50:05 node2 sshd[24111]: debug3: Incorrect RSA1 identifier
Mar 27 11:50:05 node2 sshd[24111]: debug1: read PEM private key done: type RSA
Mar 27 11:50:05 node2 sshd[24111]: debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
Mar 27 11:50:05 node2 sshd[24111]: debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
Mar 27 11:50:05 node2 sshd[24111]: debug1: private host key: #0 type 1 RSA
Mar 27 11:50:05 node2 sshd[24111]: debug3: Incorrect RSA1 identifier
Mar 27 11:50:05 node2 sshd[24111]: debug1: read PEM private key done: type DSA
Mar 27 11:50:05 node2 sshd[24111]: debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
Mar 27 11:50:05 node2 sshd[24111]: debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
Mar 27 11:50:05 node2 sshd[24111]: debug1: private host key: #1 type 2 DSA

```

---

### Post by Poma on 2012-03-27
If I'll sign in as a regular user I can't use scp to replace some configs in /etc for example

---

### Post by Poma on 2012-03-30
bump

---

