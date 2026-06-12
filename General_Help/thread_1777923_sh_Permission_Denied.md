---
title: "sh: Permission Denied"
date: 2011-06-08
forum: General Help
---

### Post by tentimes on 2011-06-08
Hi guys,

I hope someone out there can help with this difficult problem.

A user 'postgres' has had his home directory deleted. I set his home directory to a new place (opt/postgresql) and set ownership right to that and recursive directories to postgres : postgres. I have verified ownership with ls.

Now when I type ~ I cannot go to the home directory and get the error:

```
sh: /opt/postgresql: Permission denied
```

So, obviously some important info is screwed up and I don't know how to fix it. I think that this is because the user **profile** information is missing. Is there any way to make this?

User 'postgres' is the user for the PostgreSQL database, which is running fine. The trouble is that I cannot do anything when I log in as that user, so I am a bit screwed.

I would be most grateful if anyone has a solution to this. At the moment it means I cannot use the database properly, as there is no way of storing PATH information for the postgres user, so typing commands is tedious and there are no normal commands available (I can't use normal commands like ls as the user has no path etc, so I can do nothing with the user).

Thanks :)

---

### Post by ultraata on 2011-06-08
Please post following outputs:
1)cd
2)ls -la /opt/postgresql
3)cat /etc/passwd | grep postgres

---

### Post by tentimes on 2011-06-08
cd gives no reply, just goes to a new line

```

 ls -la /opt/postgresql
total 28
drwxr-xr-x  7 postgres postgres 4096 Jun  7 21:45 .
drwxr-xr-x  5 root     root     4096 Jun  7 21:25 ..
drwxr-xr-x  2 postgres postgres 4096 Jun  7 21:25 bin
drwx------ 13 postgres postgres 4096 Jun  8 15:27 data
drwxr-xr-x  6 postgres postgres 4096 Jun  7 21:25 include
drwxr-xr-x  3 postgres postgres 4096 Jun  7 21:25 lib
drwxr-xr-x  6 postgres postgres 4096 Jun  7 21:25 share

```

And for the next one:

```
$ cat /etc/passwd | grep postgres
postgres:x:1002:1002:PostgreSQL:/home/postgres:/bin/sh
```

Please note! I just changed the home directory to home/postgres to try and simplify things.

I think I know what the problem is. The home directory I am giving does not have:

.bash_logout
.bashrc
.profile

i.e. I have lost the profile.

FYI:

```
 ls -la /home/postgres
total 8
drwxr-xr-x 2 postgres root 4096 Jun  8 15:22 .
drwxr-xr-x 5 root     root 4096 Jun  8 15:22 ..

```

I realise I forgot to set the group there, but that isn't currently the problem I think?

EDIT: Done, issued: chgrp -Rv postgres /home/postgres

---

### Post by tentimes on 2011-06-08
Perhaps if I explain what happened it will shed some light on things:
[LIST]
[*]I installed a PosgreSQL Plus server from enterprisedb.com and it was a pile of poo. I uninstalled it and removed it's directory.

[*]BUT... unknown to me this program had set the postgres user home directory to inside it's program directory.

[*]I then went on to compile and install PostgreSQL 9.1 myself (I need to test some of it's features)

[*]I continued with the postgres username when setting it up, why change it, I thought? Everything went fine and it is installed and working.

[*]I then checked out the postgre user and found out the bad news - his home dir was set to the application I just removed.

[*]Now I have a user who does not have a profile or proper home directory and I am trying to rectify that for the user postgres :)
[/LIST]

---

### Post by tentimes on 2011-06-08
I know this is a stinker, so thanks for the help so far and also anyone else who can wrestle with this tricky problem ;) If I had known that the previous program set the users home directory inside it's own directories I would not have uninstalled so quickly ;)

---

### Post by tentimes on 2011-06-08
What about killing all the user processes, logging him out, then deleting the user, then create the user again, then restart everything?

---

### Post by tentimes on 2011-06-08
I have had to opt for a slightly heavy handed solution to this, but would still love to hear from YOU if you had a better one I could have followed :)

What I did was:

/etc/init.d/postgresql stop
pkill -u postgresql
update-rc.d -f postgresql remove
userdel -r postgres

So I have basically deleted the user and removed the package. I am going to reinstall the one I want from Martin Pitt's backport: [http://launchpad.net/~pitti/+archive/postgresql](http://launchpad.net/~pitti/+archive/postgresql)

---

### Post by ultraata on 2011-06-09
If cd gives no reply, then this means you have successfully changed dir to home. 
So, can you please explain the problem again?

---

