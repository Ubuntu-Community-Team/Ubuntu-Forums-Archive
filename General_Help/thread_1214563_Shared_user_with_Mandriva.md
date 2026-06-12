---
title: "Shared user with Mandriva"
date: 2009-07-16
forum: General Help
---

### Post by xiii29 on 2009-07-16
Hi !
I've two distrib install on my Laptop :
* Mandriva 2009 Spring,
* Ubuntu 9.04.

The both system have the same main user but with different id (Mand : 1000 and Ubuntu 500).

The both system shared a data directory but I've to change rigth access in order that user can write in it ... I know that I can change the umask value but ...

Is there a way to shared user's between Mandriva and/or Ubuntu ... If I have to create a new one is not a problem !

---

### Post by snkiz on 2009-07-16
You can share home directories between distro's by using the same user name and uid in both distro's. However its likely that at least some config files would conflict, if say they a both running Gnome. I've done with two Debian based distros, one was running Gnome and one Openbox so I was lucky my conflicts were easily resolved. A better option would be to keep your data in a separate dir and symlink to your home dir give you users different uids but the same gid and make your data dir writable to the group. that way you can have separate home directories for each distro and still have easy access to your data.

---

### Post by nikhilbhardwaj on 2009-07-16
you can change your uid in /etc/passwd
also if you use the same desktop environment
then you may run into conflicts

---

### Post by xiii29 on 2009-07-16
In fact, I do not want to share the home as I've a separate dir with my data. I create link in the two home.

By changing in /etc/passwd one user id, what will happen to current files of user ?

---

### Post by snkiz on 2009-07-17
if you do not want to share the home dir then you need to name them differently. Since thats all you want and you already have a separate data dir then all you would need to do is give them the same gid and make the folder writable to the group. You'd also have to change your the umask in you profile folder so that new files written to the group will keep the folders permissions, change this line:```
#umask 022
``` to:```
umask 02
```

---

