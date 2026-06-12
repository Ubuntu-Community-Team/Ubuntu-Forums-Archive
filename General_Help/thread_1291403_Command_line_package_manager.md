---
title: "Command line package manager"
date: 2009-10-14
forum: General Help
---

### Post by petersohn on 2009-10-14
I could figure out how to use the basic functions of the command line package manager (like apt-get install/remove/update/upgrade, apt-cache search etc.), but there are some things I don't know. Most importantly:
- How to list all installed packages?
- How to search among installed packages (possibly searching by installed version)?
- How to force a package to use a certain version?

---

### Post by NightwishFan on 2009-10-14
You can access help on a command by using 'man'. For example, in a terminal type:
```
man apt-get
```

This will show you the command options available. Most commands have one.

You can also use aptitude, which is a graphical frontend to apt-get.

---

### Post by ibuclaw on 2009-10-14
> **petersohn said:**
> I could figure out how to use the basic functions of the command line package manager (like apt-get install/remove/update/upgrade, apt-cache search etc.), but there are some things I don't know. Most importantly:
- How to list all installed packages?
- How to search among installed packages (possibly searching by installed version)?
- How to force a package to use a certain version?
One word.
```
aptitude
```

Regards
Iain

---

### Post by diesch on 2009-10-14
> **petersohn said:**
> I could figure out how to use the basic functions of the command line package manager (like apt-get install/remove/update/upgrade, apt-cache search etc.), but there are some things I don't know. Most importantly:
- How to list all installed packages?

```
apt-cache --installed pkgnames
```

> **petersohn said:**
> 
- How to search among installed packages (possibly searching by installed version)?

Use either aptitude or dctrl-tools


> **petersohn said:**
> 
- How to force a package to use a certain version?
See [man apt_preferences](http://manpages.ubuntu.com/manpages/jaunty/en/man5/apt_preferences.5.html)

---

### Post by jeremyswalker on 2009-10-14
> **tinivole said:**
> one word.
```
aptitude
```

regards
iain

+1

---

### Post by petersohn on 2009-10-15
> **diesch said:**
> ```
apt-cache --installed pkgnames
```
This one doesn't work. It lists all packages anyway, not just the installed ones.

> See [man apt_preferences](http://manpages.ubuntu.com/manpages/jaunty/en/man5/apt_preferences.5.html)
Thanks.

---

### Post by nothingspecial on 2009-10-15
```
dpkg --get-selections
```

will list all the packages you have installed.

```
dpkg --get-selections | grep firefox
```

will tell you if you have firefox installed, just substitute firefox for what you want to search for.

I`m not entirely sure what you mean with the 3rd one, certain versions of what?

---

### Post by justleen on 2009-10-15
> **nothingspecial said:**
> ```
dpkg --get-selections
```

will list all the packages you have installed.

```
dpkg --get-selections | grep firefox
```

will tell you if you have firefox installed, just substitute firefox for what you want to search for.

I`m not entirely sure what you mean with the 3rd one, certain versions of what?

get-selections show uninstalled or partialy installed packages too. I usually use "dpkg -l" to get a list of installed packages..

---

### Post by nothingspecial on 2009-10-15
> **justleen said:**
> get-selections show uninstalled or partialy installed packages too. I usually use "dpkg -l" to get a list of installed packages..

Absolutely correct - depends on what you want.

---

### Post by petersohn on 2009-10-15
> **justleen said:**
> get-selections show uninstalled or partialy installed packages too. I usually use "dpkg -l" to get a list of installed packages..
Thanks. That is exactly what I was looking for.

---

