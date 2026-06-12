---
title: "Error when installing software"
date: 2010-08-18
forum: General Help
---

### Post by neoargon on 2010-08-18
When I try to install any package using apt-get or synaptic ,I get the error report as given below ```
dpkg: unrecoverable fatal error, aborting:
 syntax error: unknown group 'gnokii' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)


```

Please help resolve the issue . The gnokii is a package I uninstalled earlier

---

### Post by Irony on 2010-08-18
Have you tried re-installing gnokii.

---

### Post by philinux on 2010-08-18
> **neoargon said:**
> When I try to install any package using apt-get or synaptic ,I get the error report as given below ```
dpkg: unrecoverable fatal error, aborting:
 syntax error: unknown group 'gnokii' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)


```

Please help resolve the issue . The gnokii is a package I uninstalled earlier

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/593615](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/593615)

[http://ubuntuforums.org/showthread.php?p=9324405](http://ubuntuforums.org/showthread.php?p=9324405)

---

### Post by Brandon Williams on 2010-08-18
First you want to find a list of files associated with gnokii in the statoverride file. This should do it:
```
dpkg-statoverride --list *gnokii*
```
The last item on each line is a filename. For each of those filenames run:
```
sudo dpkg-statoverride --remove <filename>
```

---

### Post by neoargon on 2010-08-18
> **Brandon Williams said:**
> First you want to find a list of files associated with gnokii in the statoverride file. This should do it:
```
dpkg-statoverride --list *gnokii*
```The last item on each line is a filename. For each of those filenames run:
```
sudo dpkg-statoverride --remove <filename>
```
 Nothing happened . In both the commands the output is 
```
dpkg: unrecoverable fatal error, aborting:
 syntax error: unknown group 'gnokii' in statoverride file

```

---

### Post by neoargon on 2010-08-18
> **philinux said:**
> [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/593615](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/593615)

[http://ubuntuforums.org/showthread.php?p=9324405](http://ubuntuforums.org/showthread.php?p=9324405)
The second link helped .Thanks

---

