---
title: "User management on a couple machines (uid and gid)"
date: 2010-01-29
forum: General Help
---

### Post by podollb on 2010-01-29
In a small network (with <5 PCs) what is the best way to manage users and groups? When I create a new user, Ubuntu automatically assigned a UID unless I specify otherwise. If I were to mount shared drives between PCs (or between a client machine and a server) I'm wondering how it handles different UIDs/GIDs associated with files (usernames almost always match across system but UIDs/GIDs do not)? Or is the best solution to just assign matching UID and GID on every machine when they are created? Or is this just magically handled via the matching usernames? I know there are heavier options but this has come up a number of times in small setups 2-5 machines at most. Thoughts?

---

### Post by bodhi.zazen on 2010-01-29
Depends on how you share files, but, yes shares and users are mapped.

NFS is a bit different then samba in how it all works, but you do not necessarily need to make all the UID the same for all users on all machines.

Now if you wish to do this, IMO, best to script it.

You can specify UID / GID, etc on the command line:

[http://linux.die.net/man/8/adduser](http://linux.die.net/man/8/adduser)

---

