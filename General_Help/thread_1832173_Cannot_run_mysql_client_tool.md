---
title: "Cannot run mysql client tool"
date: 2011-08-24
forum: General Help
---

### Post by hpng on 2011-08-24
Hello:

I have installed MySQL server via Synaptic Package Manager successfully, and I also installed MySQl administrator to check for MySQL installation.  It is all there. 
, and I ran this also, where "mysql" is a client tool:

> 

hpng@hpng-laptop:~$ sudo mysql
[sudo] password for hpng: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

I entered my ubuntu user password, and I get access error.

I have 10.04 LTS version.
WHY?

---

### Post by Wim Sturkenboom on 2011-08-24
When you installed the mysql server, you were prompted to specify a root password for the mysql root user.

```

mysql -u root -p

```
This will prompt you for the mysql root password. Enter the one that you specified

You don't need sudo to run the mysql command; it might even be dangerous if it has a bug ;) Your version of the command would have worked if you added the the -p option which will prompt you for the password. Now you have told mysql that the mysql root user does not require a password ;)

---

### Post by hpng on 2011-08-24
Previous answer helped.  Thanks.
How do i indicate problem was solved?

Where can I include my Ubuntu version and so forth to be 
displayed on my posting profile?
Thanks.

---

### Post by Wim Sturkenboom on 2011-08-24
Pleasure. You can mark the thread as solved using the thread tools just above the first post on this page.

Your profile info can be modified using the user cp (user control panel) link in the menu bar near the top of the page. For the distro, first item at the left (*_edit your details_*) and scroll down to *_additional options_*.

---

