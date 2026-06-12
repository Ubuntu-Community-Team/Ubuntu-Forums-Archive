---
title: "How To scp, ssh and rsync without prompting for password"
date: 2009-07-23
forum: General Help
---

### Post by jbailey22 on 2009-07-23
I am trying to get some scripts to run using the following method:

ROOT@source:/root> ssh-keygen -t rsa
ROOT@source:/root> cd .ssh
-------------------
[email]ROOT@source:/root/.ssh[/email]> sftp dest
Are you sure you want to continue connecting (yes/no)? yes
root@dest's password: 
sftp> put id_rsa.pub
sftp> quit
--------------------
root@dest:~# cat id_rsa_2048_b.pub >>~/.ssh/authorized_keys
---------------------
[email]ROOT@source:/root/.ssh[/email]> cd /usr/local/scripts
ROOT@source:/usr/local/scripts> vi /root/.ssh/known_hosts
ROOT@source:/usr/local/scripts> ./logger.sh 
ROOT@source:/usr/local/scripts> exit

The issue is when I hit source machines that have ssh2 on them. The dest machine is running ubuntu 9.04 server and has ssh on it. I try to cat the ssh2 pub key in and it doesn't work. Any help would be greatly appreciated. Thank you.

---

### Post by Rob_H on 2009-07-23
In old versions of OpenSSH, SSH2 keys went into a separate file called **authorized_keys2**, but I don't think that's used anymore. Still might be worth a try.

---

