---
title: "SSH is working, but SFTP is not"
date: 2010-04-24
forum: General Help
---

### Post by bone2006 on 2010-04-24
I have ubuntu server 9.10 running in which I selected the option to automatically installed security updates.  It's been running file for 4 months with both ssh and SFTP, which I installed the openssh-server.

Today I really need to upload something to the server, which is in another city and SFTP isn't working.  It's not allowing me to connected, I tried connecting with multiple FTP clients, command line...etc and on both windows and linux and SFTP just isn't working.

The only changed I've done to the configuration file was changing the port from 22 to another port and did this 4 months ago.   Been using it every few weeks since then.

Any help is appreciated it.

---

### Post by bone2006 on 2010-04-24
Update:

I edited the configuration file at /etc/ssh/sshd_config and changed PasswordAuthentication to yes, then restarted the service.

When I use filezilla or any client it's really slow establishing a connection, but at least I can transfer the important file that I need transferred.   

I'm guessing this means that ssh/SFTP will allow clear text instead of keys, so this is less secure?  I know that ubuntu 10.04 is coming out in less than a week, maybe that update will help me?

---

