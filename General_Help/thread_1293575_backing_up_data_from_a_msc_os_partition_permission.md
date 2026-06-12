---
title: "backing up data from a msc os partition permission problem"
date: 2009-10-17
forum: General Help
---

### Post by yoma819 on 2009-10-17
hello all
my mac has recently gone wrong and i want to back up the data from it!
ubuntu finds and mounts the hdd easily however i cannot access or copy my documents!
i can access the root directory but the moment i get to the personal data areas it says permission denied.
how do i change the permissions so i can copy the data off?
many thanks
yoma

---

### Post by StuartN on 2009-10-17
> **yoma819 said:**
> how do i change the permissions so i can copy the data off?

Rather than messing with the file permissions, you can change to root with **sudo bash** if you want a terminal or **gksudo nautilus** if you want a graphical file manager with root permissions.

---

### Post by yoma819 on 2009-10-17
excellent
i can now view the files in the locked directories however i cannot copy them.
i get the error:
"you do not have permissions to read"
any ideas?
many thanks
yoma

---

### Post by StuartN on 2009-10-17
> **yoma819 said:**
> "you do not have permissions to read"

In Nautilus you can see (and change, if you are root) the ownership and permissions with right-click, Properties, Permissions.

You might want to run Applications->System Tools->Configuration editor (or **gconf-editor** from the command line) and enable the key /apps/nautilus/preferences/show_advanced_permissions.

At the command line you can **ls -l** to see ownership and permissions. If you have opened a shell with **sudo bash** then you can chmod / chown them.

---

### Post by yoma819 on 2009-10-17
ok i have folled your instructions howeveer it will not allow me to change the permissions to the folders i wish to copy!
i can with all other folders just not the ones i need to copy!
any further ideas?
cheers
yoma

---

### Post by StuartN on 2009-10-17
> **yoma819 said:**
> ok i have folled your instructions howeveer it will not allow me to change the permissions to the folders i wish to copy!
i can with all other folders just not the ones i need to copy!
any further ideas?
cheers
yoma

Did you try **sudo chmod -R a+r <path>** to change file permissions, as superuser, recursively, to add read permission for all? (where <path> represent the top level folder). I do not know enough about the Mac OS, but you probably need to ensure every directory has execute permission too:

```
cd <path>
find . -name temp -type d -exec chmod a-x {} \;
```

This is just like the chmod -R above, but limits it to directories only.

---

