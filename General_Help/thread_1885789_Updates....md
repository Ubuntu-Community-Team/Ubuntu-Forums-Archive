---
title: "Updates..."
date: 2011-11-23
forum: General Help
---

### Post by layers on 2011-11-23
I have uninstalled Firefox from my system. Yet, in update manager, one of the updates that is checked up for installation is the package firefox-locale-en.

Why?

Why do I have a directory named ~/.mozilla ?

Why is that when I delete a program, it doesn't clean its act away? Why?

---

### Post by Mr Nemo on 2011-11-23
Usually when you remove a program, system files and/or the program config files will stay just in case you reinstall. You can always try to use the purge command to try and remove the rest of the files.

---

### Post by snowpine on 2011-11-23
There is no reason to uninstall Firefox in Ubuntu unless you have an extremely tiny hard drive. 

Firefox will probably be reinstalled the next time you release-upgrade (for example from 11.10 to 12.04) since it is part of the ubuntu-desktop package.

---

### Post by layers on 2011-11-23
> **Mr Nemo said:**
> Usually when you remove a program, system files and/or the program config files will stay just in case you reinstall. You can always try to use the purge command to try and remove the rest of the files.

how again?

> **snowpine said:**
> There is no reason to uninstall Firefox in Ubuntu unless you have an extremely tiny hard drive. 

Firefox will probably be reinstalled the next time you release-upgrade (for example from 11.10 to 12.04) since it is part of the ubuntu-desktop package.

Mainly because I don't want to have two browsers. I know it doesn't make a difference. It's a principle problem.

and I gave firefox as an example.

---

### Post by Slim Odds on 2011-11-24
> **layers said:**
> how again?
<cut>

```
sudo apt-get purge <package name>
```

---

### Post by lovinglinux on 2011-11-24
> **layers said:**
> I have uninstalled Firefox from my system. Yet, in update manager, one of the updates that is checked up for installation is the package firefox-locale-en.

Why?

You also need to remove the locale packages or you can try autoremove, to uninstall packages that are no longer needed.

```
sudo apt-get autoremove
```


> **layers said:**
> Why do I have a directory named ~/.mozilla ?

As mentioned already, that folder contains your user configuration files for Firefox. Those files are not removed when you uninstall applications. You need to delete them manually.

The *purge* command won't affect those files, because it only remove system config files. 

> **layers said:**
> Why is that when I delete a program, it doesn't clean its act away? Why?

Because you might just want to remove it temporarily. I would go crazy if all my personal config files would be wiped whenever I remove an application.

> **Slim Odds said:**
> ```
sudo apt-get purge <package name>
```

The purge command only removes system config files. It has no affect on Firefox profiles.

---

