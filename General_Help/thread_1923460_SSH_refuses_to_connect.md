---
title: "SSH refuses to connect"
date: 2012-02-10
forum: General Help
---

### Post by azheid on 2012-02-10
Hi Ubuntu gurus,

I have the same problem as the OP (I think), but I have way less knowledge about SSH. I cannot follow what he does to fix the error. 

My SSH verbose output is the following,
```
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to swi6.redgreengene.com [129.49.86.30] port 22.
debug1: Connection established.
debug1: identity file /home/jgardin/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-1024
debug1: identity file /home/jgardin/.ssh/id_rsa-cert type -1
debug1: identity file /home/jgardin/.ssh/id_dsa type -1
debug1: identity file /home/jgardin/.ssh/id_dsa-cert type -1
debug1: identity file /home/jgardin/.ssh/id_ecdsa type -1
debug1: identity file /home/jgardin/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_3.8.1p1  Debian-krb5 3.8.1p1-7
debug1: match: OpenSSH_3.8.1p1  Debian-krb5 3.8.1p1-7 pat OpenSSH_3.*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-1ubuntu3
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA a1:4e:02:42:ef:2f:07:4e:27:ff:ec:e6:8e:56:d1:b9
debug1: Host 'swi6.redgreengene.com' is known and matches the RSA host key.
debug1: Found key in /home/jgardin/.ssh/known_hosts:8
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: gssapi-with-mic,publickey,gssapi,keyboard-interactive
debug1: Next authentication method: gssapi-with-mic
debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1000' not found

debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1000' not found

debug1: Unspecified GSS failure.  Minor code may provide more information


debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/jgardin/.ssh/id_rsa
debug1: Authentications that can continue: gssapi-with-mic,publickey,gssapi,keyboard-interactive
debug1: Trying private key: /home/jgardin/.ssh/id_dsa
debug1: Trying private key: /home/jgardin/.ssh/id_ecdsa
debug1: Next authentication method: keyboard-interactive
```

The /etc/hosts file on the computer I am trying to ssh from looks like this
```
127.0.0.1       localhost
127.0.1.1       azheid

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

The /etc/hosts file on the remote computer looks like this
```
127.0.0.1 localhost
129.48.86.30    swi6 swi6.redgreengene.com
192.168.0.130   swi6p
192.168.0.125   swi4p
192.168.0.149   swi5p
192.168.0.125   ldap.redgreengene.com   ldap
# The following lines are desirable for IPv6 capable hosts
# (added automatically by netbase upgrade)

::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
129.49.86.25    swi4.redgreengene.com swi4
129.49.86.49    swi5.redgreengene.com swi5
192.168.0.150   cdc28p
 
```

First, do I have the same problem, and next, how do I fix it?

---

### Post by CharlesA on 2012-02-10
Moved to own thread.

Original thread is here:
[http://ubuntuforums.org/showthread.php?t=1344683](http://ubuntuforums.org/showthread.php?t=1344683)

You did not say what error you were getting, but it looks like you turned off password authentication and the server isn't accepting your key.

---

### Post by azheid on 2012-02-10
Sorry, here is my problem. I am trying to set up an automatic backup to a remote computer. I am trying to setup a rsa key for the computer and the remote computer. I made the key and the public key files and put the public key file onto the server at /home/username/.ssh/authorized_keys. The ssh between the remote computer is not accepting the rsa key login, and is prompting me for a password. The error is in the ssh verbose output
```

debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1000' not found

```

---

### Post by CharlesA on 2012-02-10
Check the permissions of:
~/.ssh/authorized_keys
~/.ssh/id_rsa.pub
~./ssh/id_rsa

on both client and server.

---

### Post by azheid on 2012-02-11
Here are the permissions on the files for the local computer


```
jgardin@azheid:~$ ll /home/jgardin/.ssh/
total 28
drwx------  3 jgardin jgardin 4096 2012-02-11 17:18 ./
drwxr-xr-x 69 jgardin jgardin 4096 2012-02-10 16:51 ../
drwxr-xr-x  2 jgardin jgardin 4096 2012-02-11 17:18 authorized_keys/
-rw-------  1 jgardin jgardin  887 2012-02-08 11:28 id_rsa
-rw-r--r--  1 jgardin jgardin  228 2012-02-08 11:28 id_rsa.pub
-rw-r--r--  1 jgardin jgardin 4984 2012-01-24 13:40 known_hosts
```

Here are the permissions on the files for the remote computer

```
justin@swi6:~$ ls -l /justin_home/.ssh/
total 0
drwxr-xr-x  2 justin users 80 2012-02-08 12:49 authorized_keys
justin@swi6:~$ ls -l /justin_home/.ssh/authorized_keys/
total 4
-rw-------  1 justin users 228 2012-02-08 12:49 id_rsa.pub

```

Please bear with me, I know very little about how ssh connections are are set up.

---

### Post by Khayyam on 2012-02-11
> **azheid said:**
> ```
justin@swi6:~$ ls -l /justin_home/.ssh/
total 0
drwxr-xr-x  2 justin users 80 2012-02-08 12:49 authorized_keys
justin@swi6:~$ ls -l /justin_home/.ssh/authorized_keys/
total 4
-rw-------  1 justin users 228 2012-02-08 12:49 id_rsa.pub

```

asheid .. authorized_keys should be a file, not a directory. Move id_rsa.pub into /justin_home/.ssh/ and remove the directory /justin_home/.ssh/authorized_keys/, rename 'id_rsa.pub' 'authorized_keys'

```
ssh user@server
cd .ssh
mv authorized_keys/id_rsa.pub ~/.ssh/
rm -f authorized_keys/
mv id_rsa.pub authorized_keys
```You should now be able to login with the key.

> **azheid said:**
> Please bear with me, I know very little about how ssh connections are are set up.

Easy mistake to make, you put the key in a directory when the file should have been in ~/.ssh.

HTH ...

---

### Post by CharlesA on 2012-02-12
That would do it.

I tend to just use ssh-copy-id now instead of creating things manually so I don't have to worry about permissions and mistakes, because I have been known to make a few when trying to get this set up. :)

---

### Post by azheid on 2012-02-15
Ok, I did what Khayyam said line by line, and the same result occurs. I then deleted authorized_keys on the remote computer (don't worry, I am the only one on the system) and used the following command
```
ssh-copy-id -i .ssh/id_rsa.pub 
Password: 
Now try logging into the machine, with "ssh 'justin@swi6.redgreengene.com'", and check in:

  ~/.ssh/authorized_keys

to make sure we haven't added extra keys that you weren't expecting.

justin@swi6.redgreengene.com
```
And I still get the same output error from ssh
```
jgardin@azheid:~$ ssh -v justin@swi6.redgreengene.com
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to swi6.redgreengene.com [129.49.86.30] port 22.
debug1: Connection established.
debug1: identity file /home/jgardin/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-1024
debug1: identity file /home/jgardin/.ssh/id_rsa-cert type -1
debug1: identity file /home/jgardin/.ssh/id_dsa type -1
debug1: identity file /home/jgardin/.ssh/id_dsa-cert type -1
debug1: identity file /home/jgardin/.ssh/id_ecdsa type -1
debug1: identity file /home/jgardin/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_3.8.1p1  Debian-krb5 3.8.1p1-7
debug1: match: OpenSSH_3.8.1p1  Debian-krb5 3.8.1p1-7 pat OpenSSH_3.*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-1ubuntu3
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA a1:4e:02:42:ef:2f:07:4e:27:ff:ec:e6:8e:56:d1:b9
debug1: Host 'swi6.redgreengene.com' is known and matches the RSA host key.
debug1: Found key in /home/jgardin/.ssh/known_hosts:8
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: gssapi-with-mic,publickey,gssapi,keyboard-interactive
debug1: Next authentication method: gssapi-with-mic
debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1000' not found

debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1000' not found

debug1: Unspecified GSS failure.  Minor code may provide more information


debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/jgardin/.ssh/id_rsa
debug1: Authentications that can continue: gssapi-with-mic,publickey,gssapi,keyboard-interactive
debug1: Trying private key: /home/jgardin/.ssh/id_dsa
debug1: Trying private key: /home/jgardin/.ssh/id_ecdsa
debug1: Next authentication method: keyboard-interactive

```

---

### Post by Khayyam on 2012-02-15
> **azheid said:**
> [...] I still get the same output error from ssh.
Yes, same error, but your ~/.ssh/authotized_keys were setup incorrectly none the less.

Anyhow, something is wrong here, I take it your keys are loaded? It looks as though it finds the id_dsa but can't use it for some reason, I can only assume the key is locked, what method are you using to add your key, ssh_agent? Did you perhaps set your key to be closed after a certain period?

So, please explain how your key is loaded, from the above it looks like ssh-copy-id asks for your key passphrase (an so it **should** be available for that shell/terminal) or was it asking for the pass for the remote machine? I've not used ssh-copy-id and so I'm not familiar with how it works.

Have you since restarted your session?

HTH ...

---

