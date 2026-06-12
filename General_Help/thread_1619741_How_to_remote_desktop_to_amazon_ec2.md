---
title: "How to remote desktop to amazon ec2?"
date: 2010-11-12
forum: General Help
---

### Post by dxxvi on 2010-11-12
Hi all,

I launch an Amazon EC2 instance (AMI: ami-508c7839 which is a Maverick server x86) with t1.micro type. I ssh to that machine and install libaudiofile0, ubuntu-desktop from the Ubuntu repository. I install nx client, node and server from [www.nomachine.com](www.nomachine.com). I say 'yes' for PasswordAuthentication in the /etc/ssh/sshd_config file, change the password of the 'ubuntu' account with sudo passwd ubuntu, restart the ssh server with sudo /etc/init.d/ssh restart. 

On my local machine which is Maverick x86, I install libaudiofile0 and nxclient. The I run nxclient to connect to that EC2 instance. The nxclient passes the 'waiting authentication', 'download the session information', 'negotiating link parameters'. Then it says "Could not yet establish the connection to the remote proxy".

Does anybody know what's wrong here?

Regards.

Solved: uncheck the disable encryption for all traffic in nxclient.

---

