---
title: "help apt-get eclipse, can't find jre installation"
date: 2006-04-02
forum: General Help
---

### Post by songo on 2006-04-02
hi there,
i'm trying to install eclipse but apt-get can't find where jre is installed. i've installed jdk so jre is on:
/usr/jdk1.5.0_06/jre

```
songo@kinomi:~$ sudo apt-get install eclipse
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  eclipse: Depends: j2re1.4 but it is not installable
E: Broken packages

```

---

### Post by testube_babies on 2006-04-02
I would install Eclipse from [eclipse.org]("http://www.eclipse.org/").  All you have to do is unpackage a tar and it should be up and running (assuming java is installed correctly).  If that doesn't work, then there's something wrong with your java installation.

---

