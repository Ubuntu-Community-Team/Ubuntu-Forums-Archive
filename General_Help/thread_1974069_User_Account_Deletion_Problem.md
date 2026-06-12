---
title: "User Account Deletion Problem"
date: 2012-05-05
forum: General Help
---

### Post by jwsicomputing on 2012-05-05
Hi i am just trying to remove a user account which i don't want.
I tried through user accounts, but just kept getting the prompt - user is logged in cant do it.
So i tried deleting the users home directory, but no luck either.

Is there a force remove command for a user account??
OR any solution is greatly appreciated!

Thanks
James

---

### Post by ajgreeny on 2012-05-05
Can you show the output from the command ```
ls -al /home
```and also the name of the user you want to delete.

---

### Post by jwsicomputing on 2012-05-05
i want to delete the user laing (Laing System Full name) and all that appears is Laing Server which is my current account

Attachement shows screen shot: But the text said:

[ATTACH]217345[/ATTACH]

laingserver@laing-server:~$ ls -al /home
total 12
drwxr-xr-x  3 root        root        4096 May  5 16:31 .
drwxr-xr-x 23 root        root        4096 May  4 08:40 ..
drwxr-xr-x 23 laingserver laingserver 4096 May  5 19:27 laingserver
laingserver@laing-server:~$

---

### Post by ajgreeny on 2012-05-05
You will have to make the new user first, but make sure that new user has full admin rights or you will be stuck when you want to install or do anything to update the system, etc etc.  However, were you aware that there was only one user on the machine, ie, **laingserver**, or did you expect another called just **laing** as well as **laingserver**?

I do not understand what you mean by > i want to delete the user laing (**[COLOR=Red]Laing System Full name[/COLOR]**) and all that appears is Laing Server which is my current accountas there is no user called laing at all on the machine.  **laingserver** is your username, and **laing-server** is the machine's hostname

So you are confusing the machine name and your username.  To make changes you will need to edit the two files **/etc/hosts** and **/etc/hostname** changing the entry "laing-server" to be what you want as the new hostname, then reboot.

If I have misunderstood, just ignore all I say here and wait for someone else to answer.

---

