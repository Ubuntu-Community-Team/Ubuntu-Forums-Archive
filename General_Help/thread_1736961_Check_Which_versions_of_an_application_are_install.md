---
title: "Check Which versions of an application are installed"
date: 2011-04-22
forum: General Help
---

### Post by amathew on 2011-04-22
Let's say that I've installed the following versions of R on my computer.
R 2.10
R 2.11
R 2.12

Is there a bash command which can be used to get a list of all versions which are installed.

I've used dpkg --get-selections | grep r-base but that just return 'r-base' and i'd have no info on the version.

Help!?

---

### Post by yetiman64 on 2011-04-22
> **amathew said:**
> Let's say that I've installed the following versions of R on my computer.
R 2.10
R 2.11
R 2.12

Is there a bash command which can be used to get a list of all versions which are installed.

I've used dpkg --get-selections | grep r-base but that just return 'r-base' and i'd have no info on the version.

Help!?

Try the command,

```
dpkg --list | grep <package-name>
``` replace <package-name> with the actual package name. 

Though the Synaptic package manager lists the installed version number in the main view panel and other versions available can be found by right clicking the entry and selecting Properties, then go to the versions tab. It depends on if you absolutely have to use terminal or not (maybe for scripting purposes).

---

### Post by Rubi1200 on 2011-04-23
The following command shows you the version and if it is installed or not (marked with _ii_ for installed or _un_ when not):

> dpkg -l *name of package*

e.g. > dpkg -l *firefox*

---

