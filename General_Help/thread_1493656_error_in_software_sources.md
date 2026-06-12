---
title: "error in software sources"
date: 2010-05-26
forum: General Help
---

### Post by g.oostema on 2010-05-26
I think i did something wrong adding a repository
I get the following error.

'E:Type 'etsky/ppa/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/irving-popovetsky-ppa-lucid.list, E:The list of sources could not be read.'

when i go to that file it is read only.
anyone can help me fix this issue?

Hope so as i cant update install anything now.

tnx

giliam

---

### Post by Soul-Sing on 2010-05-26
do you in your softwaresources a ppa with that name, you could remove it
or via (sudo) gedit /etc/apt/sources.list

---

### Post by 3rdalbum on 2010-05-26
> **leoquant said:**
> do you in your softwaresources a ppa with that name, you could remove it
or via (sudo) gedit /etc/apt/sources.list

That's won't work, the malfunctioning line is not in /etc/apt/sources.list.

I'd just advise to delete the /etc/apt/sources.list.d/irving-popovetsky-ppa-lucid.list file, either by:

```
sudo rm /etc/apt/sources.list.d/irving-popovetsky-ppa-lucid.list
```

Or by opening your file browser as root and deleting it:

```
gksudo nautilus
```

Now try adding the repository again.

The reason you can't modify that file as your ordinary user account, is because your ordinary user account can only modify files inside its home directory. You need to be root in order to modify system files; the 'sudo' and 'gksudo' (graphical sudo) commands will run programs and other commands as root.

---

### Post by g.oostema on 2010-05-26
@ 3rdalbum

tnx, removed through the sudo command and all working fine now.

Also used the other command to delete a locked folder on my desktop.

thanks for the help, super.

one question i tried to logout and login as root but cant get in.
is that not possible or did i just forget my password?

---

