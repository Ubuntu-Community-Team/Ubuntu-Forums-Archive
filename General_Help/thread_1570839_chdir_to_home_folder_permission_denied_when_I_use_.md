---
title: "chdir to home folder: permission denied when I use ssh"
date: 2010-09-08
forum: General Help
---

### Post by zarzor_2010 on 2010-09-08
Dear all
I have a strange problem

I ssh to a remote server using the username "madel" and it gives me a strange error:

Last login: Wed Sep  8 18:17:51 2010 from greece.doe.carleton.ca
Could not chdir to home directory /home/madel: Permission denied
grep: /home/madel/.bashrc: Permission denied
Preparing your .bashrc for Linux
cat: /home/madel/.bashrc: Permission denied
mv: accessing `/home/madel/.bashrc.09.08.Sep.09': Permission denied
mv: accessing `/home/madel/.bashrc': Permission denied
chmod: cannot access `/home/madel/.bashrc': Permission denied
mkdir: cannot create directory `/home/madel/Desktop': Permission denied
cp: accessing `/home/madel/Desktop/.': Permission denied

I chcked the permissions using ls:
?--------- ? ? ? ?            ? madel ls -l:

Now when I su to the root user the ls -l works fine and tell that "madel" is the owner of /home/madel

drwxr-xr-x 64 madel students 4096 Sep  7 21:26 madel


The strange thing is when I do sudo bash
and write cd ~/
it chdir to /home/madel


Can any one help me plzzzzzzzzzz

thanks in advance
Mina

---

### Post by zarzor_2010 on 2010-09-08
any help please??????????????


thx

---

### Post by zarzor_2010 on 2010-09-08
I just noticed something that can help

I am loging in to the server as domain user. means that my user name is not mentioned in the /etc/passwd file.

Can this help?


Thanx

---

### Post by bodhi.zazen on 2010-09-08
> **zarzor_2010 said:**
> any help please??????????????


thx

Please do not bump your own threads in less then 24 hours, minimum.

---

