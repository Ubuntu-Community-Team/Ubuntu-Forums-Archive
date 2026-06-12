---
title: "Modifying files through a network / permission problem"
date: 2009-07-12
forum: General Help
---

### Post by conehead77 on 2009-07-12
Situation:
A desktop computer and a netbook, connected through a local network.

What i want to do:
Work on the desktop and access files on the netbook and modify them.

Problem:
When i edit the file and try to save i get this message:
"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

So what permissions do the files need?

---

### Post by blueridgedog on 2009-07-12
How are you accessing the files on the netbook?  ssh/ftp/samba?

---

### Post by conehead77 on 2009-07-12
> **blueridgedog said:**
> How are you accessing the files on the netbook?  ssh/ftp/samba?

I made a ssh connection with "Places->Connect to Server"
In nautilus it shows as sftp.

---

### Post by blueridgedog on 2009-07-12
What are the permission of the files you are trying to edit?  You can view them by launching a terminal and then initiating an ssh connection to the server, cd to the directory containing the files and issue:

```
ls -al
```

---

### Post by conehead77 on 2009-07-12
> **blueridgedog said:**
> What are the permission of the files you are trying to edit?  You can view them by launching a terminal and then initiating an ssh connection to the server, cd to the directory containing the files and issue:

```
ls -al
```

-rw-r--r--  1 root root   52 2009-06-01 23:05 index.html

Its in the /var/www/ directory of the netbook btw.

Ok, changing permissions to 777 already worked, thanks. Now i wonder if this is a good solution.

---

### Post by blueridgedog on 2009-07-12
Well, the real issue is that root owns the file.  Changing the permissions back to the way they were (644) and changing the ownership of the file

```
chown USER:USER /var/www/index.html
```

(replace USER with the user account on the local (netbook) system that you connect as).

---

### Post by conehead77 on 2009-07-12
Worked like a charm, thanks again! Been using Ubuntu for quite a while now, but never bothered about permissions :)

---

