---
title: "SSH passwordless login not working on 9.10 x64"
date: 2010-04-27
forum: General Help
---

### Post by Quarkaholic on 2010-04-27
Hi everyone. First some background:

I am in the process of migrating a cluster for fire simulation from 32-bit Windows to x64 Karmic Koala. The software (FDS) uses LAM-MPI to start processes on "slave" machines; this means permissions must be OK to start processes. The machines ran Ubuntu 8 for a while (without being used for this software) and were later dist-upgraded.

Passwordless logins using SSH sgould solve this, no? Naturally, I have used ssh-keygen and ssh-copy-id, I have also done it manually using several tutorials, I have edited the sshd_conf file, I have checked all my file permissions, ssh -vvv shows no error but goes to password-based login anyway, and I have even mucked around with seahorse and the PAM module (without understanding much of the latter).

Nothing works: I always get a password prompt.

Am I missing something fundamental?

Is there another way?

---

### Post by bodhi.zazen on 2010-04-27
ssh -i ~/.ssh/key_name user@server

You specify a key ^^ or add it to memory with seahorse  or ssh-add (ssh agent), then

ssh user@server

---

### Post by Quarkaholic on 2010-04-27
It doesn't matter if I specify the identity:

```
fds@Nero:~$ ssh -i /home/fds/.ssh/id_rsa fds@caesar -v
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to caesar [192.168.77.206] port 22.
debug1: Connection established.
debug1: read PEM private key done: type RSA
debug1: identity file /home/fds/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug1: identity file /home/fds/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug1: Remote protocol version 2.0, remote software version lshd-2.0.4 lsh - a GNU ssh
debug1: no match: lshd-2.0.4 lsh - a GNU ssh
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client 3des-cbc hmac-md5 none
debug1: kex: client->server 3des-cbc hmac-md5 none
debug1: sending SSH2_MSG_KEXDH_INIT
debug1: expecting SSH2_MSG_KEXDH_REPLY
debug1: Host 'caesar' is known and matches the RSA host key.
debug1: Found key in /home/fds/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: password,publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/fds/.ssh/id_rsa
debug1: Authentications that can continue: password,publickey
debug1: Offering public key: /home/fds/.ssh/id_rsa
debug1: Authentications that can continue: password,publickey
debug1: Next authentication method: password
fds@caesar's password: 

```

---

### Post by Quarkaholic on 2010-04-27
I'll be damned, I didn't notice the "lshd-2.0.4 lsh" before :mad: removing this seems to have fixed everything :-p I think... :-p

---

### Post by bodhi.zazen on 2010-04-27
Good catch =)

---

### Post by Quarkaholic on 2010-04-27
Seems like LSH stuck from the earlier 8.x installation, causing weirdness. Thanks anyway! :)

---

