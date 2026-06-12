---
title: "sudo: unable to change to sudoers gid: Operation not permitted sudo: setresuid() [0,"
date: 2012-10-02
forum: General Help
---

### Post by redoxon on 2012-10-02
Hello,
I'm an Ubuntu 12.04 user. 
Today when I turned on my computer, I got the following message upon login:

"Could not update ICEauthority file /home/user/.ICEauthority"

I've been searching around how can I fix it, but still haven't found the solution. 
According to what I read, the most probable reason for this error has to do something the installation of Veetle, because this is the only thing that changed before I got this message.

I found that using the sudo chown command should fix the problem, but it's not working for me, as any sudo I mean to do, I get the following message:

sudo: unable to change to sudoers gid: Operation not permitted
sudo: setresuid() [0, 0, 0] -> [118, -1, -1]: Operation not permitted

So, any ideas on how to fix it??? I'm kind of desperate here. 

Thanks

---

### Post by GBGamer117 on 2012-10-02
Try recovery. In GRUB, go to Ubuntu Linux... [recovery mode] or something similar to that. Drop down to a root prompt. Then chown it. It should work now.
NOTE: If you have an encrypted home folder, I'm sorry, I can't help you. Also, remember to mount read write.

---

### Post by redoxon on 2012-10-02
I managed to solve it.
From the console Ctrl+Alt+F1 I logged in, then did the 
sudo chown -R user:user /home/user/.*

Every post I saw about this didn't mention the part of logging on in the console, and I'm far far away from being an expert user.

Installation of Veetle is generating this problem for many of us.

Thanks for the help.

---

