---
title: "Could not initialize the package information..."
date: 2009-06-28
forum: General Help
---

### Post by Rytron on 2009-06-28
Hi.

I recently installed Xubuntu as a second OS on a friends laptop.

I got this message:

```
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_jaunty-updates_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
```

I tried a few things. I'm not certain which one thing did the trick but all is right now. Can anyone confirm to me what fixed it?

It may have been
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

but I'm not certain.

---

### Post by Soul-Sing on 2009-06-28
```
sudo rm /var/lib/apt/lists/* -vf
```



```
sudo apt-get update
```

edit: sorry you solved it already....

---

