---
title: "Apt-get package problem - no header"
date: 2011-05-21
forum: General Help
---

### Post by marin123 on 2011-05-21
please help!
i cant update or install anything.

i have started update manager and i got an error. then i tried to update through terminal and got this:

```
marin@marincelo:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
marin@marincelo:~$ sudo apt-get upgrade -f
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
marin@marincelo:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```

any way of fixing this?

---

### Post by linuxinstalledfromhdd on 2011-05-21
sudo rm /var/lib/apt/lists/* sudo apt-get clean sudo apt-get update sudo apt-get upgrade

---

### Post by marin123 on 2011-05-21
> **linuxinstalledfromhdd said:**
> sudo rm /var/lib/apt/lists/* sudo apt-get clean sudo apt-get update sudo apt-get upgrade

so, i should remove whole /var/lib/apt/lists folder?
i know what the rest does... does apt-get generate removed files automatically?


EDIT: nevermind, i removed contents of the folder and now everything works :) thank you!!!

---

