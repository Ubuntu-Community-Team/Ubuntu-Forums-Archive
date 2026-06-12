---
title: "what is sudoers?"
date: 2009-08-10
forum: General Help
---

### Post by stlsaint on 2009-08-10
ever since i added myself to the vbox group after i installed sun virtual box...and now everytime i do anything involving sudo i get this....

stlsaint@stlsaint-laptop:~$ sudo apt-get update
[sudo] password for stlsaint: 
stlsaint is not in the sudoers file.  This incident will be reported.
stlsaint@stlsaint-laptop:~$

---

### Post by Iowan on 2009-08-10
Talking (typing?) somewhat over my head, but...
depending on how you added yourself to the vbox group, you may have *transferred* yourself to that group (out of the admin group). I can't remember which command does that by default (without proper options selected). Have you seen [this]("http://www.psychocats.net/ubuntu/fixsudo") page?

---

### Post by cariboo on 2009-08-10
You can check to see if you are a member of the admin group by opening an Applications--Accessories-->Termianl and typing:

```
groups
```

you should see something like this:

```
jim adm dialout cdrom plugdev lpadmin admin sambashare vboxusers
```

If you aren't in the admin group, use this command:

```
sudo gpasswd -a <user> admin
```

to add yourself to the group.

---

### Post by ptn107 on 2009-08-10
The way you should have added yourself:
```
sudo usermod -a -G vboxusers $USER
```

---

