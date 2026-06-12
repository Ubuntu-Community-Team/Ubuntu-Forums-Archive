---
title: "using ssh"
date: 2010-03-23
forum: General Help
---

### Post by isyan on 2010-03-23
im trying to use ssh on my web hosting to install a magento testing website but i can't connect to it..

i tried reading this [https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html]("https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html") but now im stuck with this instruction..

By default the public key is saved in the file ~/.ssh/id_dsa.pub, while ~/.ssh/id_dsa is the private key. Now copy the id_dsa.pub file to the remote host and appended it to **~/.ssh/authorized_keys2:**

i searched for the ~/.ssh/authorized_keys2 in my web hosting file manager but i didn't find it...

im confused.. can somebody please help me..

---

### Post by any.linux12 on 2010-03-23
try this howto instead: [http://pkeck.myweb.uga.edu/ssh/](http://pkeck.myweb.uga.edu/ssh/)

---

### Post by isyan on 2010-03-23
same problem... i dont know where to find this in my web hosting

scp ~/.ssh/id_dsa.pub burly:**.ssh/authorized_keys2**

---

### Post by tvbracket on 2010-03-23
Ya even I have the same problem

---

### Post by pbrane on 2010-03-23
Are you sure that your "web hosting" uses key based authentication? You have to create the keys yourself and upload them to your server. Did you create the keys on your server? If you can't find your *authorized_keys* file on your remote host then you probably don't have one. You'll have to create it. 

I created my keys on my local machine and then used *scp* to copy them to the remote. I created a *.ssh* dir on the remote host and then scp'd the local key files to *~/.ssh/authorized_keys*. I did pretty much what that tutorial said to do.

---

### Post by any.linux12 on 2010-03-24
> **isyan said:**
> same problem... i dont know where to find this in my web hosting

scp ~/.ssh/id_dsa.pub burly:**.ssh/authorized_keys2**

every user has a .ssh folder. For example, if you are with the user admin and you do the command cd (which goes to the home folder) you can do:

cd .ssh

inside that folder you will find files that help the ssh connections. If you don't have that folder, it means that the user admin has never made a ssh connection. To create the folder just do:

ssh localhost

this will ask you for the password and them the folder will be created.
If you have this basic configuration it should be easy to follow the tutorial that I indicated.

Fell free to ask more about this.

---

### Post by rnerwein on 2010-03-24
hi
if you are fighting around with ssh --> look at this ( man sshd_config ). dirves me crazy a couple of times.
 StrictModes
             Specifies whether sshd(8) should check file modes and ownership
             of the user's files and home directory before accepting login.
             This is normally desirable because novices sometimes accidentally
             leave their directory or files world-writable.  The default is
             &#8220;yes&#8221;.
that means:~/.ssh 09:48-> ls -ld .
drwx------ 2 ....
ls -l
-rw------- 1 user user ...
and so on.
ciao

---

