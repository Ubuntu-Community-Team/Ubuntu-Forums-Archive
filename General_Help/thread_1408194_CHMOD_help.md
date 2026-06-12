---
title: "CHMOD help"
date: 2010-02-16
forum: General Help
---

### Post by blazemore on 2010-02-16
I have a directory containing some files.
I'm running on a server system with no GUI.
How can I set the permissions to allow people in my *group* to be able to read and list the files in the directory, and to allow everyone else read permissions only to files they know exist (ie no listing)?

---

### Post by mcduck on 2010-02-16
```
chmod u=rwx,g=rx,o=r /path/to/your/directory
```

or:

```
chmod 754 /path/to/your/directory
```

On directories the execute permission is what defines if a user can list it's contents or not, while read permission provides access to files (if you know the file name & full path).

---

### Post by rnerwein on 2010-02-16
hi
hello mcduck
i think the guy want to something like this.
the file in the directoy should only be modifyed and listed by the owner of the directory but can be accesed by members of the group preconditioned they know the full path and the name of the file.
this will be made by.
chmod 710 hidden
ls -ld hidden
drwx--x--- 2 test richi 4096 2010-02-16 10:15 hidden
cd hidden
ls -l
ls: Öffnen von Verzeichnis . nicht möglich: Permission denied
root@tschang:~/hidden ls -l
-rw-r----- 1 test richi 10 2010-02-16 10:15 friends.txt
but
richi@tschang:~ 10:29-> vi ./hidden/friends.txt
==> this works
ciao :-)

---

