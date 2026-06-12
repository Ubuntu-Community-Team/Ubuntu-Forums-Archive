---
title: "update error"
date: 2009-08-28
forum: General Help
---

### Post by jamgalex on 2009-08-28
Hi,

Can someone help me, I have been using Ubuntu for about a month now so am still getting used to it.

When I run the update manager I get this error message

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty-updates_multiverse_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Does anyone know how to fix it.

Thanks

---

### Post by ubudog on 2009-08-28
This may work: Open a terminal (Applications>Accessories>Terminal) and type ```
sudo apt-get update
```.  Once that is done, try again.  If it still doesn't work, the reboot your computer.  Post back the results.  Good Luck!  Hope that helps! :P

---

### Post by iver2435 on 2009-08-28
also try 

```
sudo apt-get check
```

and 

```
sudo apt-get clean
```

---

### Post by ubudog on 2009-08-28
> **iver2435 said:**
> also try 

```
sudo apt-get check
```

and 

```
sudo apt-get clean
```

Yes.  Good Luck! :P

---

### Post by michy99 on 2009-08-28
If none of the above has worked, try```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

### Post by Niloc on 2009-08-29
Reading package lists... Error!                
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_jaunty_non-free_binary-i386_Packages
E: The package lists or status file could not be parsed or opened               

How do I fix this??

I have tried finding a new mirror but I always end up with the same one, is there a guaranteed correct mirror somewhere?

Niloc

---

