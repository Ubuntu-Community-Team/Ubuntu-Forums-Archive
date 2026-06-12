---
title: "USB flash drive unable to mount not Authorized"
date: 2011-04-08
forum: General Help
---

### Post by gotaug on 2011-04-08
I've found some older threads with the same problem and read a few bug reports also.  Nobody has a solution that has worked for me.

How can I get Ubuntu 10.10 to be able to use something as basic as a usb drive?

---

### Post by brawnypandora0 on 2011-05-01
BUMP!!!!!!! Why can't Ubuntu get such a simple task like this right?

---

### Post by TheHimself on 2011-05-01
Here is one thing you can do.  Open a terminal and run

```

sudo chown -R  me:me /media/

```
What I mean is to replace "me" with your username.  This makes the folder yours and resolves the authorization problem.

Unfortunately you will find this kind of nuisances in Linux.

---

### Post by TheHimself on 2011-05-01
You'd better do this with the drive attached.

---

### Post by jwmollman on 2011-06-17
Unfortunately, I have the same problem here on Debian wheezy. I tried the command above but it did not work for me.

---

### Post by wildmanne39 on 2011-06-17
> **jwmollman said:**
> Unfortunately, I have the same problem here on Debian wheezy. I tried the command above but it did not work for me.Hi,
```
sudo chown -R username:username /media/file
```

After the second username in the command /media/file is the location of your drive with your files on it.

---

