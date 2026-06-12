---
title: "Sudoers Fix Remotely"
date: 2010-09-30
forum: General Help
---

### Post by ResentfulDoom on 2010-09-30
I was trying to get some permissions to work, but accidentally messed up my /etc/sudoers file. I know how to fix the problem but, I cannot access the file to edit it. The problem is the machine is physically several hundred miles away. I use it as a server. I can access it with SSH, VNC, FTP, and SSHFS. Is there any way to fix the problem with those tools. I know allowing login as root would fix it, but all commands to enable the root account require sudo, which I cannot use.

---

### Post by bshosey on 2010-09-30
Is it possible to have some one boot to live CD? You may be able to edit the file with a Live CD.

---

### Post by WorMzy on 2010-09-30
You can fix it from a LiveCD, or by booting into recovery mode. If you can't do either of these from where you are, you're going to have to ask someone else to do it for you.

It's a simple enough fix (assuming you've just buggered up the permissions and not the content), you just need to chmod the permissions of the file to 440. You should also chown and chgrp to root if you changed the ownership in any way.

---

### Post by ResentfulDoom on 2010-10-01
I may be able to get my brother to boot with a Live CD, but he is pretty computer illiterate. Thanks. I will try.

---

