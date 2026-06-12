---
title: "file access permissions to folder in $HOME of other user"
date: 2009-07-01
forum: General Help
---

### Post by Janek Kowalik on 2009-07-01
Hi, 

I want to give full access for janek to the directory inside home directory of other user.
Well I did created group and added janek to this group then I made that group owner of the directory, then I changed rights for the group to full access. 
However I cannot go to that director being user janek. What is wrong ?


My user :
# id janek
uid=522(janek) gid=523(janek) groups=523(janek),524(nimrod)

Folder I want access to (/home/globus/.nimrod/experiments):
# ls -l /home/globus/.nimrod/
total 3760
drwxrwx--x  9 globus nimrod    4096 Jul  1 14:54 experiments


When I try to access the folder:
$ cd /home/globus/.nimrod/experiments
-bash: cd: /home/globus/.nimrod/experiments: Permission denied


Help appreciated

--
Jan

---

### Post by doas777 on 2009-07-01
can you cd to /home/globus ?
my guess is that you cannot jump to a folder that you can access, if you cannot access it;s parent. you may be able to use a link though.

---

### Post by Janek Kowalik on 2009-07-01
Nope cannot cd to /home/globus

My final aim is to have access to that folder from level of java code.

---

### Post by master_kernel on 2009-07-01
Did you reboot? The group change doesn't take effect until after a reboot.

---

### Post by doas777 on 2009-07-01
> **Janek Kowalik said:**
> Nope cannot cd to /home/globus

My final aim is to have access to that folder from level of java code.

hmm. if you want to share data amoungst multiple users, is there a compelling reason to keep that data in one users home?  

not that I'm trying to sidestep your question. Master_Kernel makes a very good point. give it a reboot if you haven't yet. does an ls -l on the /home/globus show that you should be able to get there?

---

### Post by Janek Kowalik on 2009-07-03
> **master_kernel said:**
> Did you reboot? The group change doesn't take effect until after a reboot.

I am afraid, it did not help. :/

---

### Post by akakingess on 2009-07-03
> **doas777 said:**
> can you cd to /home/globus ?
my guess is that you cannot jump to a folder that you can access, if you cannot access it;s parent. you may be able to use a link though.


+1

I don't think you can jump through folders you don't have access to to get to one you have been given permission for, you may need to look into symbolic links, or some other place to store the data in that folder. Just my $0.02.

akakingess

---

