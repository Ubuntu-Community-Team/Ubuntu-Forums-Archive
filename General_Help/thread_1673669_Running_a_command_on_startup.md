---
title: "Running a command on startup"
date: 2011-01-22
forum: General Help
---

### Post by mikeobeda on 2011-01-22
I am running Ubuntu Server 10.10, and would like it to execute a file on startup (before logging in, as most of the time, no one is logged in to the server).  I have the executable file in the home folder of a user with sudo privileges.  I understand that this is supposed to be simple, and I tried doing something with putting a file in /etc/init.d/, but I didn't know what I was doing, and therefore it didn't work.  If someone can help me do this, that would be great.

---

### Post by Slim Odds on 2011-01-22
look for a file called rc.local

---

### Post by mikeobeda on 2011-01-22
Where would this file be, and what the heck do I do with it when I find it?

---

### Post by matt_symes on 2011-01-22
Hi 

You'll find it at 

```
/etc/rc.local
```

Make sure it's executable

```
sudo chmod 755 /etc/rc.local
```

and call your script from it.

Remember, it is run by root so it will have root's environment and not yours. So use full paths and set any environmental variables it may require.

Kind regards

---

