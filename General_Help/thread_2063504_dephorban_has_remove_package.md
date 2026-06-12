---
title: "dephorban has remove package"
date: 2012-09-27
forum: General Help
---

### Post by matbos on 2012-09-27
hi,

i have problem:

i have use deborphan,
 and now i can't start virtualbox, 
i can't go with firefox to page with flash
i can't start thunderbird
and i can't go with chrome to page with flash 

i have uninstall flash player because security

i have install java 7 to try resolve this problem but now thunderbird don't work

matbos

i am french

---

### Post by jerrrys on 2012-09-27
You can try update; configure -a; install -f.  Or just manually rebuilding packages.

This is when backup is a blessing.

---

### Post by Lars Noodén on 2012-09-27
deborphan by itself does nothing.  Can you explain a little what exactly you did and how you used it?  That might help with finding a solution.

---

### Post by matbos on 2012-09-27
hi,

my command:

sudo apt-get install deborphan
sudo apt-get remove $(deborphan) --purge 
sudo apt-get autoremove --purge `deborphan` 
sudo dpkg -P `dpkg -l | grep "^rc" | tr -s ' ' | cut -d ' ' -f 2`
find /media -maxdepth 2 -name ".Trash*" -delete

---

### Post by Lars Noodén on 2012-09-27
That was pretty thorough.  It removed all the packages you added manually and then some.  

I haven't done this kind of recovery before so you will have to do reading on your own before trying.  There should be a file /var/lib/dpkg/status-old that you can use to replace /var/lib/dpkg/status with.  Or failing that use an older one from /var/backups/dpkg.status.*  From there I think, but am not sure, that it might be possible to replace /var/lib/dpkg/status and then run 'sudo apt-get dselect-upgrade' and restore what you had.

---

### Post by matbos on 2012-09-27
in other forum, somebody ask me to use the end of

/var/log/dpkg.log

it is the ending of dpkg s'operation

who can i find the removal of package in this log?

---

### Post by Lars Noodén on 2012-09-28
The format of /var/log/dpkg.log is a little hard to work with, it's a log of what has been installed.  Whereas the file /var/lib/dpkg/status (and /var/lib/dpkg/status-old) shows the state of the packages.  I think the following should work to restore your machine based on what was in /var/lib/dpkg/status-old.

```

awk '$1=="Status:" && $2=="install" {print PACKAGE " install";PACKAGE=""};$1 == "Package:" {PACKAGE=$2}' **/var/lib/dpkg/status-old** | sudo dpkg --set-selections
sudo apt-get dselect-upgrade

```

Sorry for the long [awk](http://manpages.ubuntu.com/manpages/precise/en/man1/awk.1posix.html) statement.  The package status wan't always on the second line of the record.

---

### Post by matbos on 2012-09-28
```
sudo apt-get dselect-upgradeLecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants seront ENLEVÉS*:
  fglrx-updates*
0 mis à jour, 0 nouvellement installés, 1 à enlever et 0 non mis à jour.
Après cette opération, 0 o d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n]*? o
(Lecture de la base de données... 610175 fichiers et répertoires déjà installés.)
Suppression de fglrx-updates ...
Purge des fichiers de configuration de fglrx-updates ...
update-initramfs: deferring update (trigger activated)
update-rc.d: /etc/init.d/atieventsd exists during rc.d purge (use -f to force)
dpkg*: erreur de traitement de fglrx-updates (--purge)*:
 le sous-processus script post-removal installé a retourné une erreur de sortie d'état 1
Aucun rapport «*apport*» écrit car MaxReports a déjà été atteint
                                                                Traitement des actions différées («*triggers*») pour «*initramfs-tools*»...
update-initramfs: Generating /boot/initrd.img-3.2.0-31-generic
Des erreurs ont été rencontrées pendant l'exécution*:
 fglrx-updates
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

it's not this package

do you want to have /var/lib/dpkg/status post?

---

### Post by Lars Noodén on 2012-09-28
Hmm.  I tested on a spare machine, but could only guess at your exact situation.  If you need to edit the list of packages manually you could do it like this:

```

awk '$1=="Status:" && $2=="install" {print PACKAGE " install";PACKAGE=""};$1 == "Package:" {PACKAGE=$2}' /var/lib/dpkg/status-old | sort> /tmp/x
nano /tmp/x
sudo dpkg --set-selections < /tmp/x
sudo apt-get dselect-upgrade

```

---

### Post by matbos on 2012-09-28
sorry

but who what can i find to do in nano /tmp/x?

where is the package i have deleted in past?

---

### Post by Lars Noodén on 2012-09-28
The second example captured the output of awk into /tmp/x.  That includes all the packages you had installed earlier, based on /var/lib/dpkg/status-old.  I can't read enough French to get the exact error, but if there are individual packages that you must remove before trying the re-install they can be removed manually as described above.

---

### Post by matbos on 2012-09-28
ok sorry

he have to have a package system good?
is that?



so,

why can not remove fglrx-update?

---

### Post by Lars Noodén on 2012-09-28
Maybe this step is needed first:

```

sudo dpkg --clear-selections

```

---

### Post by matbos on 2012-09-28
it's ok
```

sudo dpkg --clear-selections
-iMac:~$ awk '$1=="Status:" && $2=="install" {print PACKAGE " install";PACKAGE=""};$1 == "Package:" {PACKAGE=$2}' /var/lib/dpkg/status-old > /tmp/x
-iMac:~$ sudo dpkg --set-selections < /tmp/x
-iMac:~$ sudo apt-get dselect-upgrade
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.


```

---

### Post by Lars Noodén on 2012-09-28
The big test is whether or not it will survive a reboot now. ;)

---

### Post by Lars Noodén on 2012-09-28
> **matbos said:**
> ...
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.



If it's not adding any packages, you may have to try from /var/backups/dpkg.status.0 

```

sudo dpkg --clear-selections
awk '$1=="Status:" && $2=="install" {print PACKAGE " install";PACKAGE=""};$1 == "Package:" {PACKAGE=$2}' /var/backups/dpkg.status.0 | sudo dpkg --set-selections
sudo apt-get dselect-upgrade

```

Or even older with /var/backups/dpkg.status.1.gz using [gzip](http://manpages.ubuntu.com/manpages/precise/en/man1/gzip.1.html)

```

sudo dpkg --clear-selections
gzip -cd /var/backups/dpkg.status.1.gz  | awk '$1=="Status:" && $2=="install" {print PACKAGE " install";PACKAGE=""};$1 == "Package:" {PACKAGE=$2}' | sudo dpkg --set-selections
sudo apt-get dselect-upgrade

```

---

### Post by matbos on 2012-09-28
thank you very much

that's works

my program rebirth

but how that works?

---

### Post by Lars Noodén on 2012-09-28
Awk can be a little complicated at first glance, but once you know the parts, it's easy to read or write.

The awk part has to output a list of packages and their status.  You can see a sample of this kind of output from your own machine by using [font=Courier New]dpkg --get-selections[/font].  (That's the current status of your machine.)  But it has to use /var/lib/dpkg/status-old for input and the output is piped (|) into dpkg.  

See also 
[http://manpages.ubuntu.com/manpages/precise/en/man1/dpkg.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/dpkg.1.html)

In the status-old file the fields of the database are on different lines, but not always the same line.

```

$1=="Status:" && $2=="install" 
{print PACKAGE " install";PACKAGE=""}

```

Means find lines where the first column is equal to 'Status:' and the second column is equal to 'install'   When they are found, print whatever was stored in the variable PACKAGE, plus the string 'install'.  Then clear PACKAGE

```

$1 == "Package:" 
{PACKAGE=$2}' 

```

Mean when a line is found where the first column is equal to the string 'Package:', store the contents of the second column into the variable PACKAGE for use later.

```

/var/backups/dpkg.status.0 

```

Means read this file for input.

There are of course other ways to arrive at the same output still using awk.  It's not a perfect solution but it works in this case, if there are no problems with the data file.

---

### Post by matbos on 2012-09-28
if i understand

we have to combine two list

that the principle of awk

but what 's were the problem of my system?

how combine(awk) can resolve this problem?

---

### Post by Lars Noodén on 2012-09-28
Your commands deleted an unexpectedly large and important number of packages from your system:

```

#sudo apt-get install deborphan
#sudo apt-get remove $(deborphan) --purge 
#sudo apt-get autoremove --purge `deborphan` 
#sudo dpkg -P `dpkg -l | grep "^rc" | tr -s ' ' | cut -d ' ' -f 2`
#find /media -maxdepth 2 -name ".Trash*" -delete

```

That, as we found out, is not a safe way to use [deborphan](http://manpages.ubuntu.com/manpages/precise/en/man1/deborphan.1.html).  Or else dpkg or both.   I think what you wanted was [font=Courier New]sudo apt-get autoremove[/font], with no extra options.

Anyway, what was left was not much, few packages survived the purge.  Fortunately, the old status of packages was in /var/lib/dpkg/status-old,  /var/backups/dpkg.status.0, or  /var/backups/dpkg.status.1.gz  We had to use awk to munge the status file into a format that dpkg could use.  We used --set-selections to provide the list to the package manager and we used dselect-upgrade to act on that list.

---

