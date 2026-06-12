---
title: "get error message in update Manager"
date: 2009-07-24
forum: General Help
---

### Post by andhrooy on 2009-07-24
I am using Ubuntu 9.04 installed on  the hard drive.

When I go to system/administration/update manager. Update manager finds the packages, gives me a green tick on the install button but does not install them instead I get an error message

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can anyone please inform me how to get the update manager to work. and what that message means.

---

### Post by Soul-Sing on 2009-07-24
```
sudo dpkg --configure -a
```

this message is probabl. correct, and will fix your problem.

---

### Post by prem1er on 2009-07-24
Does this mean that during an update/install the process was interrupted and synaptic had and error?

---

### Post by Ratscallion on 2009-07-24
If you get told to run a command to try and fix it when you actually get the error, it should be common sense to run it...

---

### Post by NewbieNik on 2009-07-24
Hold on now guys, I get exactly the same error whilst trying to install or uninstall using apt-get or synaptic.
I _have_ tried the

> sudo dpkg --configure -a

and get nothing, I mean NOTHING in return.

Inital error is:-

> (Reading database ... dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `dictionaries-common': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

running install -f and --configure -a does nothing, zero, zip.
Any useful advice would be welcome

---

### Post by Ratscallion on 2009-07-25
```
dpkg --configure -a
``` doesn't usually give output, just try doing this:
```
sudo dpkg --configure -a
sudo apt-get update
``` 
If you get any errors after that, paste it here.

---

### Post by andhrooy on 2009-07-26
opened terminal entered what you typed thanks it seems to work

---

### Post by Ratscallion on 2009-07-26
:) We're glad to help!

---

