---
title: "how to remove broken packages ?"
date: 2006-03-08
forum: General Help
---

### Post by sharif_aly on 2006-03-08
how could i remove the broken packages if i can't remove it from synaptic ?

---

### Post by sharif_aly on 2006-03-08
for example i try this :> 
sudo dpkg -P gforge-db-postgresql
dpkg: status database area is locked by another process
pc1@ez:~$ sudo dpkg -P gforge-db-postgresql
(Reading database ... 80016 files and directories currently installed.)
Removing gforge-db-postgresql ...
cp: cannot stat `/etc/postgresql/pg_hba.conf': No such file or directory
dpkg: error processing gforge-db-postgresql (--purge):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 gforge-db-postgresql

and couldn't remove it ...

---

### Post by sharif_aly on 2006-03-08
all i have try yet

[http://pastebin.com/590463](http://pastebin.com/590463)

---

### Post by sharif_aly on 2006-03-08
Setting up gforge-db-postgresql (3.1-31) ...
invoke-rc.d: unknown initscript, /etc/init.d/postgresql not found.
dpkg: error processing gforge-db-postgresql (--configure):
 subprocess post-installation script returned error exit status 100
Errors were encountered while processing:
 gforge-db-postgresql
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Baum88 on 2006-04-25
...I have the same exact problem but, unforunately, no solution...

Does anyone know how to fix this?

---

### Post by jdralphs on 2006-06-06
has anyone figured out a solution yet?

---

### Post by ifokkema on 2006-06-07
[QUOTE=jdralphs]has anyone figured out a solution yet?[/QUOTE]

By reading through your errors quickly, it seems the package is not installed properly in the first place. What if you first re-install the package, and then try again to remove it?

---

### Post by cezdeville on 2007-02-20
have similiar problem (error code (1)) with spring-basedata package.
is there any way to get rid of this package?

cheers,
cezy

---

### Post by viper on 2007-02-20
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Try this thread, might help with some issues...........

---

### Post by cezdeville on 2007-02-20
i was able to help myself :D
just read more carefuly error message and found out, that apt-get is complaining that there is missing folder called "mods".
i've created such folder and unistall process proceeded without any further problem.

thanks anyway!
cheers,
cezy

---

