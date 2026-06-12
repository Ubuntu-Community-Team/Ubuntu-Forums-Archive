---
title: "Need to enter password to shutdown"
date: 2012-09-12
forum: General Help
---

### Post by Red Squirrel on 2012-09-12
I now run F@H and have it running as a different user because it just made it easier to mount the remote directory in which the work is stored (I have a central server and a common account for it).  Because it's running as a different user, now it's requiring me to enter my password when I shut down.  Is there a way to stop this?  It's not like this is a server, if it was I would not be running a GUI. ;)

---

### Post by varunendra on 2012-09-13
Just a shot in the dark - is this new user a member of adm group? To find out, use the command:
```
groups *<user id>*

```(for example: groups varun)

If not try adding him to that group:
```
sudo adduser *<user id>* adm
```

As I initially warned, it's just a shot in the dark, but won't do any harms in trying.

---

