---
title: "Can CVS server be setup on Ubuntu Desktop (i.e. not Ubuntu Server)"
date: 2010-02-26
forum: General Help
---

### Post by Joelom on 2010-02-26
I have Ubuntu Desktop 9.10

Followed

[https://help.ubuntu.com/8.04/serverguide/C/cvs-server.html](https://help.ubuntu.com/8.04/serverguide/C/cvs-server.html)

after the setup step** cvs -d /your/new/cvs/repo init**
I've checked whether /etc/xinetd.d/cvspserver file is available.

No cannot find the file any where on the build.

Can CVS Server be installed on a Desktop build (9.10) 
or do I need to get Ubuntu Server to have CVS Server going?

Thanks
Joel M

---

### Post by julipanno on 2010-02-26
You have to create the file. This is done automatically by the text editor when you issue the command to open the file. If you wish to use gedit, the command would be
```
gksu gedit /etc/xinetd.d/cvspserver
```
Then, simply paste the file's contents from the guide in there.

And, to answer your second question, the only differences between Ubuntu Desktop and Ubuntu Server are the programs that are installed per default. You can use the Desktop version as a server; it's just a matter of installing the applications you need.

---

### Post by Joelom on 2010-02-27
Thanks - that worked

---

