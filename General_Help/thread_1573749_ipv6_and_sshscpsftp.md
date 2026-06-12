---
title: "ipv6 and ssh/scp/sftp"
date: 2010-09-13
forum: General Help
---

### Post by janiskr on 2010-09-13
It is just me or scp and sftp does not know exactly how to work with ipv6 addresses

if I try: ssh user@link:local:ip:v6::address%interface i have successful login, i tried everything with scp and sftp but to no result, i always get: host cannot be resolved.

tried plain:
scp file user@link:local:ip:v6::address%interface:/

tried "-6" flag "-o User admin" same result (no result that is)

---

### Post by janiskr on 2010-09-13
forgot to add, here is the output of the command:
$ scp -vvvv -6 wtf  fe80::20c:42ff:fe72:f62b%eth3:/
Executing: program /usr/bin/ssh host fe80, user (unspecified), command scp -v -t :20c:42ff:fe72:f62b%eth3:/
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
ssh: Could not resolve hostname fe80: No address associated with hostname
lost connection

---

