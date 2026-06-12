---
title: "Permission denied (publickey)"
date: 2012-04-17
forum: General Help
---

### Post by LumbeeNDN on 2012-04-17
...yes, I know there are about a million threads out there on this, but I have tried everything and I am stumped!

I am trying to login using a password rather than using the '-i' option to use the key. 

So I have a Amazon EC2 instance of Ubuntu 10.04.

I have SSH (port 22) open on the server console.

I have PasswordAuthentication yes set in /etc/ssh/ssh_config (and restarted the server)

I can login if I use the -i option in SSH as in ssh -i .ssh/test.pem ubuntu@<IP>

Somebody gimmie some ideas!!!

---

### Post by LumbeeNDN on 2012-04-18
Just for posterity, I wanted to follow up.

Be sure you are editing /etc/ssh/sshd_config and not /etc/ssh/ssh_config when changing the line..


[LIST=1]
[*]Change to no to disable tunnelled clear text passwords
[/LIST]
 PasswordAuthentication yes
 [http://internet-security-tips.com/blog/2010/what-is-the-difference-between-ssh_config-and-sshd_config/](http://internet-security-tips.com/blog/2010/what-is-the-difference-between-ssh_config-and-sshd_config/)

---

