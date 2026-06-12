---
title: "shutdown -r now"
date: 2010-06-13
forum: General Help
---

### Post by mack4 on 2010-06-13
I'm running Ubuntu 8.04.1 and I need some help. 

I'm trying to reboot the machine remotely over ssh.

Pls see the following dialogue:
root@dedicated:~# shutdown -r now

Broadcast message from [email]root@dedicated.com[/email]
	(/dev/pts/0) at 8:56 ...

The system is going down for reboot NOW!

This all looks great and is exactly what I asked for, but the system doesn't reboot.

I'm thinking there is a process running which is stopping the shutdown? But I can't find it. 

I also can't find the log which is written when shutting down, is there on? There appear to be no errors that I can find in the files in /var/log/

---

