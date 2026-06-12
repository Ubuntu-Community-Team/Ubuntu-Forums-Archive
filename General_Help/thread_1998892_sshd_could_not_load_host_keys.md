---
title: "sshd: could not load host keys"
date: 2012-06-07
forum: General Help
---

### Post by gstecca on 2012-06-07
Hi. I am try to run sshd on Ubuntu 12.04.

When trying to launch sshd I get the following error

guglielmo@erasmus:~$ /usr/sbin/sshd
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
Could not load host key: /etc/ssh/ssh_host_ecdsa_key

I have already tried to re-create the host keys with

sudo ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key
sudo ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key
sudo ssh-keygen -t ecdsa -f /etc/ssh/ssh_host_ecdsa_key[FONT=monospace]
[/FONT]/etc/init.d/ssh start 

but this didn't help. I get this bug report

guglielmo@erasmus:~$ /usr/sbin/sshd -ddd 
debug2: load_server_config: filename /etc/ssh/sshd_config 
debug2: load_server_config: done config len = 683 
debug2: parse_server_config: config /etc/ssh/sshd_config len 683 
debug3: /etc/ssh/sshd_config:5 setting Port 22 
debug3: /etc/ssh/sshd_config:9 setting Protocol 2 
debug3: /etc/ssh/sshd_config:11 setting HostKey /etc/ssh/ssh_host_rsa_key 
debug3: /etc/ssh/sshd_config:12 setting HostKey /etc/ssh/ssh_host_dsa_key 
debug3: /etc/ssh/sshd_config:13 setting HostKey /etc/ssh/ssh_host_ecdsa_key 
debug3: /etc/ssh/sshd_config:15 setting UsePrivilegeSeparation yes 
debug3: /etc/ssh/sshd_config:18 setting KeyRegenerationInterval 3600 
debug3: /etc/ssh/sshd_config:19 setting ServerKeyBits 768 
debug3: /etc/ssh/sshd_config:22 setting SyslogFacility AUTH 
debug3: /etc/ssh/sshd_config:23 setting LogLevel INFO 
debug3: /etc/ssh/sshd_config:26 setting LoginGraceTime 120 
debug3: /etc/ssh/sshd_config:27 setting PermitRootLogin yes 
debug3: /etc/ssh/sshd_config:28 setting StrictModes yes 
debug3: /etc/ssh/sshd_config:30 setting RSAAuthentication yes 
debug3: /etc/ssh/sshd_config:31 setting PubkeyAuthentication yes 
debug3: /etc/ssh/sshd_config:35 setting IgnoreRhosts yes 
debug3: /etc/ssh/sshd_config:37 setting RhostsRSAAuthentication no 
debug3: /etc/ssh/sshd_config:39 setting HostbasedAuthentication no 
debug3: /etc/ssh/sshd_config:44 setting PermitEmptyPasswords no 
debug3: /etc/ssh/sshd_config:48 setting ChallengeResponseAuthentication no 
debug3: /etc/ssh/sshd_config:63 setting X11Forwarding yes 
debug3: /etc/ssh/sshd_config:64 setting X11DisplayOffset 10 
debug3: /etc/ssh/sshd_config:65 setting PrintMotd no 
debug3: /etc/ssh/sshd_config:66 setting PrintLastLog yes 
debug3: /etc/ssh/sshd_config:67 setting TCPKeepAlive yes 
debug3: /etc/ssh/sshd_config:74 setting AcceptEnv LANG LC_* 
debug3: /etc/ssh/sshd_config:76 setting Subsystem sftp  /usr/lib/openssh/sftp-server 
debug3: /etc/ssh/sshd_config:87 setting UsePAM yes 
debug1: sshd version OpenSSH_5.9p1 Debian-5ubuntu1 
debug1: could not open key file '/etc/ssh/ssh_host_rsa_key': Permission  denied 
Could not load host key: /etc/ssh/ssh_host_rsa_key 
debug1: could not open key file '/etc/ssh/ssh_host_dsa_key': Permission  denied 
Could not load host key: /etc/ssh/ssh_host_dsa_key 
debug1: could not open key file '/etc/ssh/ssh_host_ecdsa_key':  Permission denied 
Could not load host key: /etc/ssh/ssh_host_ecdsa_key 
debug1: setgroups() failed: Operation not permitted 
debug1: rexec_argv[0]='/usr/sbin/sshd' 
debug1: rexec_argv[1]='-ddd' 
debug3: oom_adjust_setup 
Set /proc/self/oom_score_adj from 0 to -1000 
debug2: fd 3 setting O_NONBLOCK 
debug1: Bind to port 22 on 0.0.0.0. 
Bind to port 22 on 0.0.0.0 failed: Permission denied. 
debug2: fd 3 setting O_NONBLOCK 
debug3: sock_set_v6only: set socket 3 IPV6_V6ONLY 
debug1: Bind to port 22 on ::. 
Bind to port 22 on :: failed: Permission denied. 
Cannot bind any address. 
guglielmo@erasmus:~$ 


Could anybody please help me? Thanks!

Guglielmo

---

### Post by wojox on 2012-06-07
Are you trying to connect to a remote machine? What are you trying to do?

---

### Post by ptn107 on 2012-06-07
Are your permissions correct?

```
user@user-host:/etc/ssh$ ls -la
total 176
drwxr-xr-x   2 root root   4096 Jun  7 10:04 .
drwxr-xr-x 139 root root  12288 Jun  7 10:04 ..
-rw-r--r--   1 root root 125749 Apr  2 07:48 moduli
-rw-r--r--   1 root root   1669 Apr  2 07:48 ssh_config
-rw-r--r--   1 root root   2489 Jun  7 10:04 sshd_config
-rw-------   1 root root    672 Jun  7 10:04 ssh_host_dsa_key
-rw-r--r--   1 root root    611 Jun  7 10:04 ssh_host_dsa_key.pub
-rw-------   1 root root    227 Jun  7 10:04 ssh_host_ecdsa_key
-rw-r--r--   1 root root    183 Jun  7 10:04 ssh_host_ecdsa_key.pub
-rw-------   1 root root   1679 Jun  7 10:04 ssh_host_rsa_key
-rw-r--r--   1 root root    403 Jun  7 10:04 ssh_host_rsa_key.pub
-rw-r--r--   1 root root    302 Jan 10  2011 ssh_import_id
```

---

### Post by codemaniac on 2012-06-07
Are you trying to start up the ssh server ?

```
sudo service ssh start
```

---

