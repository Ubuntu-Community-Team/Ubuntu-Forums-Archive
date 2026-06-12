---
title: "Unable to connect to SFTP using new SSH account"
date: 2009-09-21
forum: General Help
---

### Post by Jobis on 2009-09-21
Hello,

Earlier today I figured out how to create new users. Then I figured out how to make sure they could connect through SSH. What I haven't figured out, however, is how to make sure they can connect through SFTP (that is, SSH). I've added my new user to the "sftp" group and verified that it can indeed connect, and run commands, through SSH in a terminal window.

But when I try to connect using the "Connect to server..." menu option in Gnome/Nautilus (top panel, under "Places") I fail. I get an error:

> Cannot display location "sftp://username@example.com/"

ssh program unexpectedly exited

A fellow employee gets a similar error when attempting to connecting from some Windows SFTP client. I am running Ubuntu 9.04 and the server is running Ubuntu Server. The terminal prints "Linux 2.6.18-128.1.1.el5.028stab062.3 #1 SMP" when connecting through SSH.

A lot of googling hasn't helped. Help?

---

### Post by Jobis on 2009-09-22
This solved itself overnight, I have no idea why.

---

