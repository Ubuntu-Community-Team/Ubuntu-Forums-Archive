---
title: "Can't access .profile file!"
date: 2011-10-15
forum: General Help
---

### Post by lygmoo on 2011-10-15
I need to enter JAVA_HOME variable in .profile file which should be located inhome directory. When I try to create one in the /home/lygmoo/ it says that this name is already taken, so the file exists.
When I try to access the file through the terminal with su permissions I get bash access denied.

```
lygmoo@lygmoo-desktop:~$ cd '/home/lygmoo' 
lygmoo@lygmoo-desktop:~$ sudo su
[sudo] password for lygmoo: 
root@lygmoo-desktop:/home/lygmoo# /.profile
bash: /.profile: Access denied

```

Please help.

---

### Post by LKjell on 2011-10-15
lygmoo should own that file so try to access without root.

/.profile is a file in /

If you do have permission problems then try

sudo chown lygmoo:lygmoo ~/.profile
chmod 644 ~/.profile
To revert read and write access to lygmoo.

---

### Post by lygmoo on 2011-10-15
Thank you for your help and for quick response. Didn't work for me though.

```


lygmoo@lygmoo-desktop:~$ sudo chown lygmoo:lygmoo ~/.profile
[sudo] password for lygmoo: 
lygmoo@lygmoo-desktop:~$ chmod 644 ~/.profile
lygmoo@lygmoo-desktop:~$ ~/.profile
bash: /home/lygmoo/.profile: Access denied

```

---

### Post by LKjell on 2011-10-15
That is because you want to execute the file. You need to use a program to edit the file. Like nano, vim, gedit etc.

---

### Post by WorMzy on 2011-10-15
There is no such file as /.profile (unless you created one).

Try running (as your normal user, not root):

```
gedit ~/.profile
```

---

### Post by lygmoo on 2011-10-16
> **WorMzy said:**
> There is no such file as /.profile (unless you created one).

Try running (as your normal user, not root):

```
gedit ~/.profile
```

Thank you. It helped.)

---

