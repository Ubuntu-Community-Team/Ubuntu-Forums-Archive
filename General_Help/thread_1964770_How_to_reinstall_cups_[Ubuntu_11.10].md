---
title: "How to reinstall cups [Ubuntu 11.10]"
date: 2012-04-24
forum: General Help
---

### Post by antibus on 2012-04-24
Hello all,

I uninstalled cups because I thought reinstalling of cups would solve my printer problems since I read this somewhere. But this is an other problem. ;)

I found two solution to install cups back again. But I get the following output

```
sudo apt-get install cups
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cups : Depends: libcups2 (>= 1.4.4-3~) but it is not going to be installed
        Depends: libcupscgi1 (>= 1.4.2) but it is not going to be installed
        Depends: libcupsdriver1 (>= 1.4.0) but it is not going to be installed
        Depends: libcupsimage2 (>= 1.4.0) but it is not going to be installed
        Depends: libcupsmime1 (>= 1.4.0) but it is not going to be installed
        Depends: libcupsppdc1 (>= 1.4.0) but it is not going to be installed
        Depends: ghostscript but it is not going to be installed
        Depends: cups-client (>= 1.4.6-5ubuntu1.4) but it is not going to be installed
        Depends: cups-ppdc but it is not going to be installed
        Recommends: cups-driver-gutenprint but it is not going to be installed
        Recommends: ghostscript-cups but it is not going to be installed
 libgtk2.0-0 : Depends: libcups2 (>= 1.4.0) but it is not going to be installed
               Recommends: libgtk2.0-bin but it is not going to be installed
 ubufox : Depends: xul-ext-ubufox but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

or

```
sudo apt-get install cupsys cupsys-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cupsys-client is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Unable to locate package cupsys
E: Package 'cupsys-client' has no installation candidate

```

After searching a couple of hours I haven't find a solution for that problem. It would be nice if somebody can help me.

Best regards...

---

### Post by Habitual on 2012-04-24
You *could* try reconfigure first...?
```
sudo dpkg-reconfigure cups
```

---

### Post by antibus on 2012-04-24
> **Habitual said:**
> You *could* try reconfigure first...?
```
sudo dpkg-reconfigure cups
```

Thanks for the fast reply, but I already have deleted cups by using the Ubuntu software center. So I think this soluten doesn't solve my problem...?

EDIT
I have tried your advice....

```
sudo dpkg-reconfigure cups

/usr/sbin/dpkg-reconfigure: cups is broken or not fully installed
```

---

