---
title: "Ridiculous SSH problem"
date: 2011-04-22
forum: General Help
---

### Post by bluegreen7hi on 2011-04-22
Ok so I just installed Ubuntu 10.10 Server Edition. On the very first boot, everything seems to run perfectly. I can SSH into it from any remote computer with no problems. However, the installation of certain things calls for a system reboot, which 2 days ago never would have been a problem. But now for some reason, the SSH server only wants to work on the very first boot of a clean install. After I reboot it, I get the **ssh: connect to host 192.168.0.180 port 22: No route to host** error. The absurd part is sshd is running! I've even tried restarting sshd, restarting the server, and using both 64 and 32 bit installs. The only way I can get anything to connect to it is by using **ssh localhost**. It won't even let me connect using the IP on the local machine! SOMEONE please help. This is driving me crazy and ruining my entire infrastructure. Any help greatly appreciated. Thanks.

---

### Post by oracle2b on 2011-04-22
check your /etc/hosts.deny file to see if there is something that shouldn't be there .

you could probably have a firewall issue. 

If all else fails try purging the sshd install/configs & reinstalling. 

> sudo apt-get purge openssh-server && sudo apt-get install -y openssh-server

---

