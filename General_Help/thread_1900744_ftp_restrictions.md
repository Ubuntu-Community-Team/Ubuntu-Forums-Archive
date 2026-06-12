---
title: "ftp restrictions"
date: 2011-12-27
forum: General Help
---

### Post by gacy on 2011-12-27
Dear all
How can I restrict access to an ftp server on linux from only specific IP addresses?

---

### Post by Lars Noodén on 2011-12-27
You can use IP Tables for that kind of restriction.

You might also want to reconsider the continued use of FTP and look at SFTP instead.

[http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

[http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)

---

### Post by gacy on 2011-12-28
Actually it is SFTP I am using with filezilla. The problem is that I can sftp from one pc to my linux machine, but from another pc (in the same network) I cannot. This is why I thought that maybe I had restricted the access to the linux machine by ip addresss, so I need to know how to add another ip adress which can sftp to the linux machine. So, how can I use the IP Tables to add the new ip address? I did see the help but it was not clear to me.

---

### Post by 2F4U on 2011-12-28
Since you are using ssh you may wish to look at denyhosts

[http://www.ubuntugeek.com/securing-ssh.html](http://www.ubuntugeek.com/securing-ssh.html)

It is also useful to automatically block repeated failed login attempts.

---

### Post by The Cog on 2011-12-28
By default, there are no restrictions on what can connect to SSH service. Unless you have configured a firewall (using iptables, ufw, gufw or other firewall configuration utility), then firewallingis not the problem. 

When you say this other PC cannot connect, what problem does it report? Can it even ping the SSH server? I'm thinking there may be some underlying network problem.

---

