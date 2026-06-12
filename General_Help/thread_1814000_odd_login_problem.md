---
title: "odd login problem"
date: 2011-07-28
forum: General Help
---

### Post by jgrosch on 2011-07-28
I'm new with Ubuntu but I am a long time FreeBSD user so I am confused as to why this is happening. I have created a user, jmartin, using the Users Administration GUI tool. The tool created the home directory /home/jmartin and this is found in /etc/passwd. I can su to this user like so;

  % su - jmartin

and I am now jmartin with the home directory as /home/jmartin. When I move the home directory using usermod like so

  % usermod -d /usr2/home/jmartin -m jmartin

The directory is moved and /etc/passwd entry is updated however when I try to become jmartin using su as before I get

  No directory, logging in with HOME=/

I've been reading through the man pages but I've not found an answer. What am I missing ?

---

### Post by lkjoel on 2011-07-28
> **jgrosch said:**
> I'm new with Ubuntu but I am a long time FreeBSD user so I am confused as to why this is happening. I have created a user, jmartin, using the Users Administration GUI tool. The tool created the home directory /home/jmartin and this is found in /etc/passwd. I can su to this user like so;

  % su - jmartin

and I am now jmartin with the home directory as /home/jmartin. When I move the home directory using usermod like so

  % usermod -d /usr2/home/jmartin -m jmartin

The directory is moved and /etc/passwd entry is updated however when I try to become jmartin using su as before I get

  No directory, logging in with HOME=/

I've been reading through the man pages but I've not found an answer. What am I missing ?
Could you give me the output of these Terminal commands?
```
ls /usr2
ls /usr2/home
ls /usr2/home/jmartin
```

---

### Post by jgrosch on 2011-07-28
berkeley% ls /usr2
Berkeley-usr3-dump  home  JuniperOldDisk  lost+found  Other  PostalBox
berkeley% ls /usr2/home
clightfoot  jgrosch      jlight   mary   tom     ziest.orig
eagoldman   jgrosch.orig  jmartin  susan  ziest
berkeley% ls /usr2/home/jmartin
Desktop    Downloads         Music     Public      Videos
Documents  examples.desktop  Pictures  Templates

---

### Post by fdrake on 2011-07-28
correct if I am wrong but you are trying to change an user account while it's still running?
from man
```
CAVEATS
       You must make certain that the named user is not executing any processes when this command is being executed if
       the users numerical user ID, the users name, or the users home directory is being changed.  usermod checks this
       on Linux, but only check if the user is logged in according to utmp on other architectures
```

---

### Post by jgrosch on 2011-07-28
> **fdrake said:**
> correct if I am wrong but you are trying to change an user account while it's still running?
from man
```
CAVEATS
       You must make certain that the named user is not executing any processes when this command is being executed if
       the users numerical user ID, the users name, or the users home directory is being changed.  usermod checks this
       on Linux, but only check if the user is logged in according to utmp on other architectures
```


Thanks but, no. The user was created as a test and it is NOT running any process.

---

