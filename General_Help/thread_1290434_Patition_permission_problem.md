---
title: "Patition permission problem"
date: 2009-10-13
forum: General Help
---

### Post by Teabicky on 2009-10-13
Hi

When i try to copy a folder into my newly partitioned internal hard drive I get this message.

> The folder "*folder name*" cannot be copied because you do not have permissions to create it in the destination.
 
 I know that it is a simple matter of changing the permissions but I am not sure how to do it.  The partition is called dev/sdb1 and it is mounted as /media/linux.

---

### Post by Teabicky on 2009-10-13
Mr Bump

---

### Post by Teabicky on 2009-10-13
I found this thread that held the solution to my problem

[http://ubuntuforums.org/showthread.php?t=697118](http://ubuntuforums.org/showthread.php?t=697118)

---

### Post by beastrace91 on 2009-10-13
You need to give your default user account permission to use the folder.

```
sudo chown myusernamehere /media/linux
```

Obviously replace "myusernamehere" with the user name you use to log into Ubuntu.

On a side note if you ever need to copy files just once or twice some where instead of chowning said folder you can just run ```
gksudo nautilus
``` which will be able to edit ANY files on the system (be careful with this one hehehe)

~Jeff

---

### Post by Teabicky on 2009-10-13
Thank you for that nice and clear reply.

---

