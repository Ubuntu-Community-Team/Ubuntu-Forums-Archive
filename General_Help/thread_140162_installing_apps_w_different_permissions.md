---
title: "installing apps w/ different permissions"
date: 2006-03-05
forum: General Help
---

### Post by chocolatetoothpaste on 2006-03-05
I want to install an application, but I want a different user to have permissions to it instead of root.  How can I do this without changing perms on a ton of different files?

---

### Post by steve.horsley on 2006-03-05
Although you need root permission to install applications in places like /usr/share, /opt, /usr/local, applications that are inatalled there are normally installed such that they can be read and executed by everybody. So you should not have to change any permissions at all. 

Unless I misunderstand what your intentions are.

---

### Post by chocolatetoothpaste on 2006-03-05
Well, just to clarify, I am installing icecast2 so I can stream internet radio.  There are various files and directories associated with the program, and unless I change the permissions, I can't access them.  For exmaple, when I get the server all setup, I then run it.  Then, in a browser, I type [http://locahost:8001/admin/stats.xsl](http://locahost:8001/admin/stats.xsl)     - This gives me a status on the server.  Now, when I installed the program, the owner was icecast2 or something.  So I had to go in and change ownership on ALL files to my username.  I more or less just want to install the program, with the owner being me.

---

### Post by aysiu on 2006-03-05
Even if another user has ownership of a file (or folder), if you set the permissions so that others can read and execute that file (or folder), there's no reason to change ownership of it.

Nevertheless, if you feel the need to change ownership, that's not a big deal. Let's say your folder with all your files is in /usr/local/bin/icecast2, just go to Applications > Accessories > Terminal and type ```
sudo chown -R chocolatetoothpaste:chocolatetoothpaste /usr/local/bin/icecast2
```

---

### Post by ice60 on 2006-03-08
maybe you heard this when it came out the day you first posted about this. it's a podcast about installing icecast, is it the same as  icecast2 :confused: 

[http://www.twatech.org/eps/twat076.mp3](http://www.twatech.org/eps/twat076.mp3)

from here
[http://www.twatech.org/](http://www.twatech.org/)

BTW, if you haven't heard the mp3 you won't believe how good it is, i'm listening now. it's Dan from The Linux Link Tech Show

---

