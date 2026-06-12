---
title: "Search  already installed software"
date: 2009-06-25
forum: General Help
---

### Post by swerdna on 2009-06-25
Hi, I've been trying to find a command line term that will search the already installed software. For example how do I find which packages contain the fragment "samba" in the software name are installed, including the version number.

In Suse we would use like this:
```
rpm -qa | grep samba
```
and if perhaps we wanted to find if samba and/or cifs was installed we might use like this:
```
rpm -qa | egrep "samba|cifs"
```

I tried a few things that I dug out of "man aptitude", but I didn't seem to quite get a good solution, and there are other package managers in Ubuntu. So I'm not sure which is the best for this CLI task in Ubuntu.

Can you tell me what command and syntax might work well for Ubuntu?

Thanks
swerdna

---

### Post by loomsen on 2009-06-25
dpkg -l is equal to rpm -qa

aptitude search is pretty handy imo, unfortunately it doesn't show the version. So, if it's up to that, dpkg -l is prlly what you want. aptitude, however, is useful as it shows installed and not installed packages (dpkg shows only ii (installed) and rc (resid config))

If you know the name of the package your looking for and want some more detailed info try aptitude show foobar

apt-cache is pretty useful too, tho I don't use it. Got familiar with aptitude (well, actually I define aliases for each OS to be the same, so no matter if it's fedora, bluewhite64 or debian, yup will always run <packagemanager> update, yumi will install and yur will remove, yus search and so on.)

---

### Post by VCoolio on 2009-06-25
Try these:

aptitude show pkg
(show details on package)

apt-cache policy pkg
(show if pkg is installed +version +updates)

dpkg -l | grep pkg
(check if pkg is installed)

dpkg-query -l | grep pkg
(check version of installed package pkg)

dpkg --get-selections | grep pkg
(check if pkg is installed and where)

---

### Post by swerdna on 2009-06-25
fabulous -- thanks ppl -- just what I needed

---

### Post by loomsen on 2009-06-25
> **VCoolio said:**
> Try these:
dpkg -l | grep pkg

dpkg-query -l | grep pkg

These do exactly the same

> 
dpkg --get-selections | grep pkg
(check if pkg is installed and where)
dpkg --get-sel only shows installed packaged, pinned packages and packages you marked for deinstallation. Doesn't show IF neither WHERE a pkg is, so this command is pretty useless (unless you want to generate a list of your installed packages which is easier to proceed from command line...)

---

