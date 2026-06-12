---
title: "how to set a global umask"
date: 2006-02-08
forum: General Help
---

### Post by michael_salcher on 2006-02-08
I'd like to share a folder between two users and therefore I'd like to to set the umask to 002 to ensure all users in a certain group have read and write access.
Yet I can't figure out how to set the umask for a user (or all users) so it's recognized by nautilus and the gnome terminal.
I set it in:

 /etc/profile
/etc/login.defs
~.bash_profile 

but that only seems to effect tty1, tty2 etc. but not nautilus nor the gnome terminal.

any ideas?

---

### Post by lamego on 2006-02-08
Changing /etc/profile should be efficient after a reboot...

---

### Post by blackwell on 2006-02-13
its gnomeVFS bug 

[http://bugzilla.gnome.org/show_bug.cgi?id=327249](http://bugzilla.gnome.org/show_bug.cgi?id=327249)

i hope it will be solved soon
---------

if anyone now how to fix it please post it here

---

### Post by vsiege on 2008-01-04
m trying to create a community directory that all users have all access to .... does this bug pertain to 7.10 as well? or is there another way to do this

---

