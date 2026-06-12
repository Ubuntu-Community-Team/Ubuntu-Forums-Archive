---
title: "SSH keys"
date: 2010-03-14
forum: General Help
---

### Post by paopao on 2010-03-14
I want to step up key authentication because it's safer, especially since I'm only going to have a handful of users connecting to a server from a handful of computers - all which I own completely.

I followed the guide here:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

It's rather simple and I was able to get key authentication to work for my account (paopao).

Here is a sample from "ssh -vvv ds9"
```
debug1: Next authentication method: publickey
debug1: Offering public key: /home/paopao/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-rsa blen 533
debug2: input_userauth_pk_ok: fp **:**:**:**:**:**:**:**:**:**:**:**:**:**:**:**
debug3: sign_and_send_pubkey
debug1: Authentication succeeded (publickey).

```

However, when I follow the same exact steps for the other account (arina) it doesn't work.
```
debug1: Next authentication method: publickey
debug1: Trying private key: /home/arina/.ssh/identity
debug3: no such identity: /home/arina/.ssh/identity
debug1: Offering public key: /home/arina/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/arina/.ssh/id_dsa
debug3: no such identity: /home/arina/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).
```

If I compare the files to see if anything is missing.  "Tribble" is the desktop computer, where I'm sshing *from*.  "ds9" is the server computer.
```
paopao@tribble:~/.ssh$ ls -la
total 20
drwx------  2 paopao paopao 4096 2010-03-14 21:05 .
drwxr-xr-x 45 paopao paopao 4096 2010-03-14 20:59 ..
-rw-------  1 paopao paopao 3239 2010-03-14 21:05 id_rsa
-rw-r--r--  1 paopao paopao  736 2010-03-14 21:05 id_rsa.pub
-rw-r--r--  1 paopao paopao 1964 2010-03-06 17:45 known_hosts

```
```
arina@tribble:~/.ssh$ ls -la
total 20
drwx------  2 arina arina 4096 2010-03-14 21:07 .
drwxr-xr-x 34 arina arina 4096 2010-03-13 22:57 ..
-rw-------  1 arina arina 3243 2010-03-14 21:07 id_rsa
-rw-r--r--  1 arina arina  735 2010-03-14 21:07 id_rsa.pub
-rw-r--r--  1 arina arina  884 2010-03-03 17:07 known_hosts

```

```
paopao@ds9:~/.ssh$ ls -la
total 16
drwx------ 2 paopao paopao 4096 2010-03-14 21:05 .
drwxr-x--- 8 paopao paopao 4096 2010-03-01 12:49 ..
-rw------- 1 paopao paopao  736 2010-03-14 21:05 authorized_keys
-rw-r--r-- 1 paopao paopao  442 2010-03-03 17:08 known_hosts

```
```
arina@ds9:~/.ssh$ ls -la
total 16
drwx------ 2 arina arina  4096 2010-03-14 21:07 .
drwxrwx--- 7 arina paopao 4096 2010-03-03 17:10 ..
-rw------- 1 arina arina   735 2010-03-14 21:07 authorized_keys
-rw-r--r-- 1 arina arina   884 2010-02-21 20:49 known_hosts

```
(/home/arina is part of paopao's group so that I'd have access (yeah, I know I should make a special group for that).  It doesn't change anything, I tested that).



So, the point is.  I don't see any reason why this shouldn't work for the other account?  If anything, "arina" is not a sudoer, but I don't see why that would make a difference.

Any help would be greatly appreciated!  Thanks!

---

### Post by Brandon Williams on 2010-03-16
You have to remove group write permission for arina's home directory on ds9. ssh doesn't consider ~arina/.ssh secure if its parent directory is writable by someone other than arina.

---

### Post by paopao on 2010-03-16
Wow, that totally worked.

Thanks!

---

