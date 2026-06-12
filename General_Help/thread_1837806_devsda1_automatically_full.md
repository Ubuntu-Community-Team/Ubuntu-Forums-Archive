---
title: "/dev/sda1 automatically full"
date: 2011-09-02
forum: General Help
---

### Post by rafiqasad on 2011-09-02
Hello everyone, I am new to ubuntu. I am facing a very strange problem. Suddenly something went wrong with my ubuntu web server.  with df -h command the output is 


root@develop:/var/log# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              23G   22G  8.0K 100% /
tmpfs                 495M     0  495M   0% /lib/init/rw
varrun                495M  540K  494M   1% /var/run
varlock               495M     0  495M   0% /var/lock
udev                  495M  132K  495M   1% /dev
tmpfs                 495M     0  495M   0% /dev/shm
lrm                   495M  2.5M  492M   1% /lib/modules/2.6.28-19-server/volatile
/dev/sda6              48G   41G  4.4G  91% /home
overflow              1.0M  8.0K 1016K   1% /tmp

I delete the files from var/log directory and make some space but
after sometime again Available memory is zero. Now I don't know what to do. Please guide me with your experiences. 

Best Regards,
Rafiq Ahmed

---

### Post by TeoBigusGeekus on 2011-09-02
Before deleting the log files, try reading them to see what's causing them to grow up to such a large size.

---

### Post by rafiqasad on 2011-09-02
Thanks for your reply.
sudo apt-get clean and sudo apt-get autoclean command but no effect. I only delete the gz files. Is this the problem of log files only or some other problem may cause this issue ??

---

### Post by dcstar on 2011-09-03
> **rafiqasad said:**
> Thanks for your reply.
sudo apt-get clean and sudo apt-get autoclean command but no effect. I only delete the gz files. Is this the problem of log files only or some other problem may cause this issue ??

As you have already been told, **look** in the log files and see what the messages are.

---

### Post by SavageWolf on 2011-09-03
Does your web site allow the users to upload files or anything?

---

