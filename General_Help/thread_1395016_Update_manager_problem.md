---
title: "Update manager problem"
date: 2010-01-31
forum: General Help
---

### Post by Ignace De La Trinite on 2010-01-31
I have one problem with update manager
He doesn't want to run. and I can not installer any program.
When I run update manager he gives me one message

Message:

[SIZE=4][COLOR=Red]Could not initialize the package information[/COLOR][/SIZE][COLOR=Red]

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/hr.archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'[/COLOR]


[COLOR=Black]Help!!!![/COLOR]

---

### Post by milton1 on 2010-01-31
You should be able to reset this manually. Open a terminal (I think it is under accesories ->terminal in gnome) and type in the following:
```

sudo apt-get update && sudo apt-get dist-upgrade

```
you will be prompted for your password, then the system will update the package lists and download and update new packages.

---

### Post by MelDJ on 2010-01-31
try [http://ubuntuforums.org/archive/index.php/t-357256.html](http://ubuntuforums.org/archive/index.php/t-357256.html)

---

