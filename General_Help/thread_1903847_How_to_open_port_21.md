---
title: "How to open port 21"
date: 2012-01-03
forum: General Help
---

### Post by Sailor-Moon on 2012-01-03
I have an ubuntu machine set up.
I have configured an FTP server on this, but can not connect to it from any other FTP client.

I know there is no firewall by default, but I have read that some ports are set to closed by default, so how can I check port 21 is open and change it to open if it is closed. Thank you in advance

---

### Post by mcduck on 2012-01-03
Unless you have set up a firewall and closed some ports yourself, there is  nothing in Ubuntu preventing the connection.

Perhaps check the server's settings, make sure it's configured to allow connections from outside and not just from localhost. Also depending on what kind of network you are using, check the configurations of your router. And if you are trying to access the server from outside of your network, you'll probably have to redirect traffic to port 21 to your server in your router's configuration.

---

### Post by luvshines on 2012-01-03
On the server itself you can check if 21 port is listening or not> netstat -an | grep 21

From the outside machine(if it's linux machine) you can use 'nc' command to check if 21 port is reachable > nc -zv <server-ip> 21

---

### Post by Sailor-Moon on 2012-01-03
Thanks for the quick reply.

I have a page of information now, all with connected and 21 highlighted.

I have since my last post installed vsftpd

I can't see in the config file where to add users and passwords.
I've read a few how to guides, but they seem to concentrate on only allowing immedieate anon access.

Anyone any idea how to set up users and passwords for vsftpd?

Thanks in advance

---

### Post by luvshines on 2012-01-03
I think ftp will refer the users present in the system(/etc/passwd) file by default. So you'll have to add more users into your server which will then act as ftp users.

---

### Post by Sailor-Moon on 2012-01-03
Thank you.
Sorry, I don't know how to set this to solved

---

### Post by Lars Noodén on 2012-01-03
> **luvshines said:**
> I think ftp will refer the users present in the system(/etc/passwd) file by default. So you'll have to add more users into your server which will then act as ftp users.

The drawback to that is that FTP transmits the usernames and passwords and whole rest of the session unencrypted over the net.  That makes it a good idea to [stop using FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) and [start using SFTP instead](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/).  You can get SFTP as part of the package [OpenSSH-Server](apt://openssh-server) and SFTP clients include FileZilla, Nautilus and Dolphin.

As far as opening ports goes, if you have no firewall, the port will be opened automatically by the listening service.

---

### Post by rjf1 on 2012-01-04
> **Sailor-Moon said:**
> Thank you.
Sorry, I don't know how to set this to solved

You can mark this thread as [solved] under 'Thread tools' at the top right area of the page

---

### Post by Sailor-Moon on 2012-01-04
Thank you

---

