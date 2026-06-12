---
title: "Can't runn Update Manager!"
date: 2010-02-23
forum: General Help
---

### Post by LarryDa on 2010-02-23
When I try to run Update Manager I get an error.
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '--2010-02-23' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'


since this is a read only, what do I do next!

LarryDa

---

### Post by michy99 on 2010-02-23
Post the output of```
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by byStanderone on 2010-02-23
...you can take a look also at this:
[http://ubuntuforums.org/showthread.php?t=1406518](http://ubuntuforums.org/showthread.php?t=1406518)

---

### Post by 3rdalbum on 2010-02-24
Remove /etc/apt/sources.list.d/medibuntu.list (you need to do this as root). You can either hit Alt-F2 and type 'gksudo nautilus' and go to the file and remove it, or run this command:

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

Try adding the Medibuntu repository again.

And then update your package list by hitting the Reload button in Synaptic, or run this command:

```
sudo apt-get update
```

---

