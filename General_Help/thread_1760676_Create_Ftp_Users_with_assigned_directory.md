---
title: "Create Ftp Users with assigned directory"
date: 2011-05-17
forum: General Help
---

### Post by eyalmmm on 2011-05-17
Hello 
i wanted to make some ftp users that will be hooked to directory and wont be able to move backward and to see the system files

ex 
user : Eyal
Directory : /home/Eyal/Eyal
so he cant get to /home/Eyal
but he can go to /home/Eyal/Eyal/cstrike
Thank u

---

### Post by btindie on 2011-05-17
> **eyalmmm said:**
> Hello 
i wanted to make some ftp users that will be hooked to directory

What you want is to chroot your users.

Take a look at this [tutorial]("http://www.wikihow.com/Setup-vsftpd-FTP-on-Ubuntu-Linux").

Under VSFTPD that's chroot_local_user, point no. 20 in the tutorial.

---

### Post by jfreak53 on 2011-05-17
Now you can do that or, if you are wanting a quick solution:

> sudo apt-get install webmin

Install webmin and let it do all the dirty work!  After installing webmin you will need to install an FTP server before using it if one isn't already installed:

> sudo apt-get install pure-ftpd

Or another such FTP server that webmin supports.

---

### Post by eyalmmm on 2011-05-17
i want to make alot of user and to put for each user directory he couldnt get backward is that it?

---

### Post by eyalmmm on 2011-05-17
> **jfreak53 said:**
> Now you can do that or, if you are wanting a quick solution:



Install webmin and let it do all the dirty work!  After installing webmin you will need to install an FTP server before using it if one isn't already installed:



Or another such FTP server that webmin supports.

i have problem my user isnt sudoer and i dont know how to make him sudoer he was sudoer i installed webmin before some days and now he isnt sudoer please help me

---

