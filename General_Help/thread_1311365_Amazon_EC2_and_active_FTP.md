---
title: "Amazon EC2 and active FTP"
date: 2009-11-02
forum: General Help
---

### Post by KayakJim on 2009-11-02
I posted this on Amazon's EC2 forums but am not getting any traction and am hoping someone here might be able to help.

I have an Amazon EC2 m1.large instance running Ubuntu 8.04 Hardy Server 64-bit and am trying to connect via active FTP to a Windows NT server.

The NT server does not support a passive connection.

Using either a command line FTP client or within a PHP script, I have the same results. I am able to connect and login but any "action" commands (e.g. ls, dir, get) returns the following error:

421 Service not available, remote server has closed connection

I believe the Amazon EC2 firewall is causing this problem. I have opened ports 1-65535 for tcp traffic and that did not resolve the issue so I'm not sure what else could be the problem.

Any help would be greatly appreciated.

---

### Post by KayakJim on 2009-11-03
A small bump in the hopes that someone has an idea what else I need to check.

---

### Post by morningboat on 2009-11-03
This looks more likely that your remote NT server blocks the data connection channel. Try to close the firewall on the NT server, or make some router's port mapping to enable the PASV mode on NT server.

---

### Post by KayakJim on 2009-11-04
Thank you for the reply morningboat.

Unfortunately I do not have any privileges on the NT server and the administrator is not willing to enable PASV mode on it. That was the first thing I ask them to do when I first encountered problems connecting.

Some additional information that I uncovered last night. I have a second Ubuntu server that is not in the Amazon EC2 cloud and was able to connect without issue. As such the problem has something to do with the way Amazon is either firewalling or routing traffic. Naturally I need the Amazon instance to make the connection and perform the processing otherwise my life would be too easy. :D

Would you possibly have any other suggestions / ideas?

---

### Post by morningboat on 2009-11-04
You may try to use some more Firewall friendly FTP protocols for the file transfers, such as SFTP and WebDav. Or you can use Amazon S3 as the intermediate place to exchange the data. Some tools, such as CrossFTP, JetS3t, etc. should work for this purpose.
Otherwise, you should consult the EC2's forum to check for their specific firewall's setting.

---

