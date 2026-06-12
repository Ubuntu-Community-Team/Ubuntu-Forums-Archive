---
title: "Error, can't update!"
date: 2009-09-19
forum: General Help
---

### Post by arashiko28 on 2009-09-19
I spent a couple of days without internet and now I have this error message when trying to update:

> Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.


Any ideas?

---

### Post by drs305 on 2009-09-19
Open Synaptic or Software Sources (System, Administration, Synaptic/Software Sources) and get to the repository settings. In Synaptic, Settings, Repositories. Note the repositories you have selected in the "Ubuntu Software", "Third Party" or "Other Sources" and "Updates" tabs and untick them. After deselecting them, reselect all previously enabled repositories.

This will remove those lists and then restore them from their source. If there was an error in the list on your computer, a good copy should be downloaded when you reselect them. If you are sure of the repository generating the error, it is only necessary to deselect and reselect that specific one. In this case, if only the one security file is corrupt, you should be able to untick and retick the "security" repository to regenerate a good list. 

Hit "Reload" to refresh the lists.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by arashiko28 on 2009-09-19
> **drs305 said:**
> Open Synaptic or Software Sources (System, Administration, Synaptic/Software Sources) and get to the repository settings. In Synaptic, Settings, Repositories. Note the repositories you have selected in the "Ubuntu Software", "Third Party" or "Other Sources" and "Updates" tabs and untick them. After deselecting them, reselect all previously enabled repositories.

This will remove those lists and then restore them from their source. If there was an error in the list on your computer, a good copy should be downloaded when you reselect them. If you are sure of the repository generating the error, it is only necessary to deselect and reselect that specific one. In this case, if only the one security file is corrupt, you should be able to untick and retick the "security" repository to regenerate a good list. 

Hit "Reload" to refresh the lists.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

Can't do what you suggest, because I get another error message and then closes itself when I press OK.
> [COLOR="Red"]E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.[/COLOR]


---

### Post by drs305 on 2009-09-19
It's also possible it is a bad status file. This should replace the status file with its desginated backup. Depending on how old the backup is, it may or may not contain the same error.
```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad 
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status 
sudo apt-get update

```

This set of commands will back up the original and replace it with the backup. If this doesn't work, we can escalate the corrective action, but try this first.

**ADDED:** Have you tried changing servers? (Especially in conjunction with the previous post.)

---

### Post by arrange on 2009-09-19
Probably a corrupt file (see the error message). Move the file and run update, the file should recreate itself.```
sudo mv /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_main_binary-amd64_Packages ~/
sudo apt-get update
```

---

### Post by arashiko28 on 2009-09-23
> **drs305 said:**
> It's also possible it is a bad status file. This should replace the status file with its desginated backup. Depending on how old the backup is, it may or may not contain the same error.
```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad 
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status 
sudo apt-get update

```

This set of commands will back up the original and replace it with the backup. If this doesn't work, we can escalate the corrective action, but try this first.

**ADDED:** Have you tried changing servers? (Especially in conjunction with the previous post.)


No good :(

---

### Post by arashiko28 on 2009-09-23
> **arrange said:**
> Probably a corrupt file (see the error message). Move the file and run update, the file should recreate itself.```
sudo mv /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_main_binary-amd64_Packages ~/
sudo apt-get update
```

I get the next message and still can't update.

> mv: cannot stat `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_main_binary-amd64_Packages': No such file or directory


When choosing regular update I get the same:

> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_jaunty_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by arrange on 2009-09-23
It's not the same error message... What do you have in you *lists* folder?```
head -1 /var/lib/apt/lists/*Packages
```

---

### Post by arashiko28 on 2009-09-23
> **arrange said:**
> It's not the same error message... What do you have in you *lists* folder?```
head -1 /var/lib/apt/lists/*Packages
```

This is what I get:

> ~$ head -1 /var/lib/apt/lists/*Packages
==> /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-amd64_Packages <==
Package: acroread

==> /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-amd64_Packages <==
Package: abiword

==> /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_binary-amd64_Packages <==
Package: a2mp3

==> /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-amd64_Packages <==
Package: drdsl

==> /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-security_main_binary-amd64_Packages <==
Package: abrowser

==> /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-security_multiverse_binary-amd64_Packages <==
Package: flashplugin-installer

==> /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-security_restricted_binary-amd64_Packages <==
Package: linux

==> /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-security_universe_binary-amd64_Packages <==
Package: abrowser-3.1

==> /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-amd64_Packages <==
Package: 2vcard

==> /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_main_binary-amd64_Packages <==
Package: abrowser

==> /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_multiverse_binary-amd64_Packages <==
Package: flashplugin-installer

==> /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-amd64_Packages <==
Package: linux

==> /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_universe_binary-amd64_Packages <==
Package: abrowser-3.1

==> /var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_jaunty_main_binary-amd64_Packages <==
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">


---

### Post by arashiko28 on 2009-09-23
Problem solved. Once I unchecked wine from the 3rd party software list, problem solved :) Thanks to all of you for your help.

---

### Post by lovestopsfear on 2009-11-25
> **drs305 said:**
> It's also possible it is a bad status file. This should replace the status file with its desginated backup. Depending on how old the backup is, it may or may not contain the same error.
```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad 
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status 
sudo apt-get update

```

This set of commands will back up the original and replace it with the backup. If this doesn't work, we can escalate the corrective action, but try this first.

**ADDED:** Have you tried changing servers? (Especially in conjunction with the previous post.)


i had the same problem and this worked for me. thanks drs! :)

---

