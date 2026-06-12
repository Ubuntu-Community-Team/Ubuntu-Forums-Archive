---
title: "User nobody?"
date: 2011-03-16
forum: General Help
---

### Post by phlegyas on 2011-03-16
Hello,
I have two folders created during a sync via Samba whicha are sid to be owned by the user nobody.
I don't have writing permissions on them.
Do you have any idea to delete them or to change the owner?

Thanks

---

### Post by r-senior on 2011-03-16
To change ownership, use chown from a terminal:

$ cd <the_offending_directory>
$ sudo chown phlegyas.phlegyas file1 file2

You'll need to enter your password.

The reason for duplicating your name after the dot, is that the second part is the group. A default Ubuntu install creates a group with the same username as you specified as your name.

And for interest: [http://en.wikipedia.org/wiki/Nobody_%28username%29]("http://en.wikipedia.org/wiki/Nobody_%28username%29")

---

### Post by lithopsian on 2011-03-16
nobody is a default user for some purposes such as NFS.

---

### Post by sisco311 on 2011-03-16
Hi and welcome to the forums!

If the directories are in your home directory, you should be able to delete them. 

If you want to change the owner and group of the files, then open your file manager as root:

Press Alt+F2 or open a terminal and run:
```
gksu nautilus
```

Navigate to the directory, select the directories, right click on them and select *Properties*. In the *Permissions* tab change the owner and group, then click the *Apply Permission to Enclosed Files* button.

---

### Post by sisco311 on 2011-03-16
> **r-senior said:**
> 
$ cd <the_offending_directory>
$ sudo chown phlegyas.phlegyas file1 file2


A period (`.') is a valid character in a username. Using a period as a separator is deprecated. One should use a colon (`:'):
```
chown user:group file
```

If the group is missing after the colon, then it's changed to the login group:
```

chown user: file  # is the equivalent of:
chown user:initial-login-group file

```

---

### Post by phlegyas on 2011-03-17
gksu nautilus worked well!!

Thanks

---

