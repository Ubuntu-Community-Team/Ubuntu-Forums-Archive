---
title: "How to create a sftp server"
date: 2011-02-21
forum: General Help
---

### Post by unbuntunewb on 2011-02-21
Hello,

I would like to turn my desktop into an sftp server that I can access remotely and in addition allow those close to me access too by giving them a user account but I would like to restrict them to a specific folder. I dont want people poking around my computer. How does one do this? How do I do it graphically?

thank you so much

---

### Post by deconstrained on 2011-02-21
[Set up OpenSSH](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html) and run it as a service, and be sure to set the following option in /etc/ssh/sshd_config:
```
Subsystem sftp /usr/lib/openssh/sftp-server
```
(this may actually be enabled by default)

If by remotely you mean away from home, you **ABSOLUTELY MUST** disable "PermitRootLogin" (it is not safe to have that enabled!) and (1) Forward an unconventional/"unprivileged" port for SSH on your wireless router, i.e. 50-something-thousand, and/or (2) Install, configure and run the 'denyhosts', to protect your computer from brute-force SSH attacks.

As for people poking around inside your computer: if you mean that there are others logged in, you can manage that by setting the group ownership and permissions on your files and folders, and only adding users to specific unprivileged groups.

You can use Nautilus's interface to set permissions; right click on a file/folder, select 'Properties' and go to the permissions tab. Also, you can administer users and groups using GNOME's tool for this task, which can be found in System -> Administration -> Users and Groups.

---

### Post by unbuntunewb on 2011-02-21
is there a wiki/manual on this? I have never attempted this before. Is this a daunting task?

---

### Post by deconstrained on 2011-02-21
Yes, and yes. I specifically linked to a wiki page, but that article is not all that you'll need to know; properly setting up and running an SSH server requires editing the following configuration files in /etc:

hosts.allow
hosts.deny
ssh/sshd_config
(See the manual pages on these files for more information.)

Nevertheless, OpenSSH is the bread and butter of administering hosts remotely, so setting up an SSH server is perhaps one of the most common tasks in the world of computers. That being said, if you do some google searching and spend some time going over the documentation you'll find a wealth of information on the topic. 

Also, SSH, if you don't configure and secure it properly, can be a massive security hole, so be warned. Simple things like disabling root login or using a port other than 22 (the default SSH port) can greatly increase the security, but sometimes using more sophisticated tools such as an IP blocking daemon like DenyHosts is warranted.

---

