---
title: "sshd could not be stopped"
date: 2010-07-01
forum: General Help
---

### Post by cccccccc on 2010-07-01
Hello,

 I'll tell you friends, I really almost smashed my head to desk today. I have latest openssh-server. you know the classic star/stop scripts:

sudo /etc/init.d/ssh start/stop

But when I wrote this stop command, everything looks good, except sshd was still running. I looked into script it uses start-stop-deaemon to kill through pid. The script always kills process, but immediately, new process of sshd was emerged (by it self - with new process ID)! I don't get it. I'm sick of my not understanding of the proglem! The new process of sshd has parent with id 1 (init). How is this possible? How does it come, that ssh can not be turn off and nobody has noticed or complain about it? Or what am I doing wrong?

After 2 hours of googling I managed to find this command:

sudo service ssh stop

and ssh finally got killed. Yeahh! After issuing this command /etc/init.d/ssh start/stop work correctly. But only to restart of system. Is this some king of super-uber command and we should not user /etc/init.d/ scripts anymore?

The strange thing is, ssh is run by itself after system start-up (without being in /etc/rc...).

Please, help me with this confusion.

---

### Post by The Cog on 2010-07-01
This came up recently in another thread:
[http://ubuntuforums.org/showthread.php?p=9531897#post9531897](http://ubuntuforums.org/showthread.php?p=9531897#post9531897)

---

### Post by cccccccc on 2010-07-01
Wow, thank you man. I thought that /etc/rc is sacred. But I see I have to learn more. I just hope Ubuntu informed about this "start/stop" change.

---

