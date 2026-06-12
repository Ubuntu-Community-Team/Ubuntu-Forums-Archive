---
title: "HELP! I can't use sudo!"
date: 2011-05-31
forum: General Help
---

### Post by redbikemaster on 2011-05-31
When I try to use sudo, I get this error message.
```

sudo: /etc/sudoers is owned by uid 1000, should be 0
sudo: no valid sudoers sources found, quitting

```

Please help!

---

### Post by doas777 on 2011-05-31
did you take ownership of your sudoers file? lets restore it to its default ownership and permissions.

ok, first open a terminal as root, by hitting Alt + F2, and entering
```
gksu gnome-terminal
```then in the shell that pops up, enter:
```

chown root:root /etc/sudoers
chmod 440 /etc/sudoers

```then open a new terminal (however you usually do it) and see if sudo works again.

remember, always use visudo to edit your sudoers.
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by ajgreeny on 2011-05-31
Nice idea, but I think if sudo does not work, neither will gksu, so I suspect the command you suggest using gksu won't work either.

I think you may need to do all this from recovery mode, so from grub choose that option (usually second in the grub menu), go to a command line and then run those commands direct from the command line interface that you will get.

---

### Post by Noz3001 on 2011-05-31
Can you ```
su -
``` and then chown the file?

---

### Post by redbikemaster on 2011-05-31
OK, I tried [doas777]("http://ubuntuforums.org/member.php?u=451394")'s advice while in recovery mode per [ajgreeny]("http://ubuntuforums.org/member.php?u=27747")'s suggestion and I now can use sudo but I get this, which I suppose isn't that bad considering sudo is working again.
```

/etc/sudoers.d/README is owned by uid 1000, should be 0

```

Thanks for the help so far!

---

### Post by doas777 on 2011-05-31
> **ajgreeny said:**
> Nice idea, but I think if sudo does not work, neither will gksu, so I suspect the command you suggest using gksu won't work either.

I think you may need to do all this from recovery mode, so from grub choose that option (usually second in the grub menu), go to a command line and then run those commands direct from the command line interface that you will get.
usually when I get messages about sudo not working (usually a host name not found in the hosts file), gksu still works for me. if the op is lucky, that is the case, if not, recovery mode is the way to go.

@op, here is what your permissions should be for /etc/sudoers and /etc/sudoers.d/
```

user@host:~$ ls -al /etc | grep sudoers
-r--r-----   1 root     root       609 2010-05-31 14:53 sudoers
drwxr-xr-x   2 root     root      4096 2011-01-22 00:21 sudoers.d

user@host:~$ ls -al /etc/sudoers.d
total 20
drwxr-xr-x   2 root root  4096 2011-01-22 00:21 .
drwxr-xr-x 146 root root 12288 2011-05-31 02:10 ..
-r--r-----   1 root root   819 2010-04-13 13:37 README

```so based on this, try these modified commands:
```

chown root:root /etc/sudoers 
chmod 440 /etc/sudoers
chown -R root:root /etc/sudoers.d
chmod  755 /etc/sudoers.d 
chmod  440 /etc/sudoers.d/*

```recovery mode works as well as any other root shell.

---

### Post by redbikemaster on 2011-05-31
Done. And fixed.

Thread is now marked as solved!

---

### Post by TheMixtureMedia on 2012-03-27
Hey there I am having the same issues but when I do what needs to be done it says the files are read only. I am not sure how to fix my issue.

---

### Post by flemur13013 on 2012-03-27
"the files are read only"

Edit: even after copying that I misread it as ownership...my reply was bogus, but it won't let me delete it (?), so maybe try "sudo chmod +r filename" ... via LiveCD/whatever, then the others.

Edit2: if that doesn't work, make sure the disk isn't mounted read-only (use gparted or palimpsest).

---

### Post by rajhanschinmay on 2012-08-20
I am facing the same problem, gksu is not opening. Getting this msg repeatedly.

sudo: /etc/sudoers is owned by uid 1000, should be 0
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin


Kindly let me know what I can do. Tried all soln., none found working.

TY.

---

### Post by Lars Noodén on 2012-08-20
rajhanschinmay, boot into recovery mode and then fix the permissions for /etc/sudoers and co.

```

chown root:root /etc/sudoers 
chmod 440 /etc/sudoers
chown -R root:root /etc/sudoers.d
chmod  755 /etc/sudoers.d 
chmod  440 /etc/sudoers.d/*

```

---

### Post by dimilinux on 2013-01-22
Hello Ubuntu community,

I am new on Linux. After 15 years i decide to change OS. Proud of it.

OK. Here is my problem: 


:~$ sudo /etc/init.d/apache2 restart
sudo: /etc/sudoers is owned by uid 1000, should be 0
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin


I was try to solve it, use instructions from here, but i didn't success.

I was try to install Joomla on my Ubuntu following these steps:
[http://vipinkrsahu.blogspot.com/2009/11/how-to-install-joomla-in-linux-ubuntu.html]("http://http://vipinkrsahu.blogspot.com/2009/11/how-to-install-joomla-in-linux-ubuntu.html")

During installation I changed permissions. I was clicking in /etc/apache2 folder.

Also, i have lock sing over apache2 folder now.

Can someone help me?

---

