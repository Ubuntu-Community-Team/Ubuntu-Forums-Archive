---
title: "changed ssh port, but still can't connect"
date: 2010-08-09
forum: General Help
---

### Post by pythonscript on 2010-08-09
I changed the ssh port on my ftp server from 22 to 2995 by editing the /etc/ssh/ssh_config file, uncommenting the line, etc. I restarted the ssh server (/etc/init.d/ssh restart) but when I try to connect on the new port, it says "connection refused."

Also, I can still connect on port 22... I ran

```
sudo ufw allow 2995
``` but I still get connection refused. 

Help... I'm not sure what to do. Thank you!

EDIT:  ufw is started, as well, through 

```
sudo service ufw start
```

---

### Post by efflandt on 2010-08-09
ssh_config configures defaults for ssh client.  Perhaps you need to edit /etc/ssh/sshd_config for the daemon (server).

---

### Post by pythonscript on 2010-08-09
Thank you. I changed the port in /etc/ssh/sshd_config to 2995 (on the server) and now I get a "no route to host error." I restarted the ssh service on the server, and then rebooted the entire server. Still no luck. These are on the same LAN.

---

### Post by efflandt on 2010-08-09
Unless you set something up for that host in your ~/.ssh/config on the client end, you would connect to it with **ssh -p 2995 ip_address** (or username@ip_address if a different user on destination).

I recently set up IPCop w/squid on an old K6-2/400 w/128 MB RAM, and it only allows ssh into it as root on port 222, so I had to **ssh -p 222 root@192.168.6.20** (and that worked from Ubuntu).  For safety I put ~/ssh/authorized_keys2 in root's home w/600 permission and allow ssh login with keys only (not passwords).

You cannot use a hostname unless it resolves in your DNS or it is in /etc/hosts of your client PC, or you give it a name in ~/.ssh/config of your client PC, for example"

Host ftp
Port 2995
HostName [ip_address or hostname]

Then you could simple connect to it with simply **ssh ftp** (see: man ssh_config)

---

