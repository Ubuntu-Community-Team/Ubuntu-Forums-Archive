---
title: "Could not initialize the package information Errors"
date: 2011-06-15
forum: General Help
---

### Post by Eric.B on 2011-06-15
I'm having a problem getting package manager to run:

```
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_maverick-updates_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
```Using apt-get update:
```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```Does anyone know what would cause this to suddenly fail?  Or how to fix it?

Thanks!

---

### Post by dstu on 2011-06-15
I'm having a similar message:

```
'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'
```

Here is the contents of that file:

```
dstu@Benedict:~$ cat /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en
<HTML><HEAD><TITLE>Cisco Systems Inc. Web Authentication Redirect</TITLE><META http-equiv="Cache-control" content="no-cache"><META http-equiv="Pragma" content="no-cache"><META http-equiv="Expires" content="-1"><META http-equiv="refresh" content="1; URL=https://1.2.3.4/login.html?redirect=archive.canonical.com/ubuntu/dists/natty/partner/i18n/Translation-en.gz"></HEAD></HTML>
```

The [https://1.2.3.4/login.html](https://1.2.3.4/login.html) is the URL that I get redirected to in order to log in on the network I'm using (at work).  This only started happening after I logged in through that network, although it seems to be happening on my home network now too.

---

### Post by carlonzo on 2011-06-15
Let you try this [http://ubuntuforums.org/showthread.php?p=10806539](http://ubuntuforums.org/showthread.php?p=10806539)

It should work!

---

### Post by dstu on 2011-06-15
Worked like a charm!  Thank you sir!

---

### Post by Eric.B on 2011-06-15
```
sudo rm /var/lib/apt/lists/*
sudo apt-get update
```

worked great.  thanks.

---

