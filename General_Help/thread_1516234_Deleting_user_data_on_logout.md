---
title: "Deleting user data on logout"
date: 2010-06-23
forum: General Help
---

### Post by J V on 2010-06-23
Setting up an old PC, publicly accessible, putting this into .bash_logout and then making it 444... It's the only computer most of these people have that's secure enough for banking etc...

This is on #!...

```
cd && ls -a | grep -vE "^\.(bash_logout|profile)$" | rm -rf
``````
cp /etc/defaultusersettings/ ~
```Will this (In theory) work? Should shred everything but the logout script every time someone logs out and copy the default settings back every login.

Potential problems:
1. [s]files with ".bash_logout" in their names will not be deleted, want to get it completely clean every time.[/s] (Used regex with "^\.bash_logout$")
2. Will the system work properly with all those files missing? It should just recreate them every time but...
3. [s]Are there any other ways "Standard" users could permanently write files to the disc...[/s] (Only in the TMP folder, but that's erased every time the system starts up again anyway)
4. I recently experimented and realized shred only works on individual files... in addition, rm -rf deletes folders regardless of their permissions... This just got a lot more complicated...

---

