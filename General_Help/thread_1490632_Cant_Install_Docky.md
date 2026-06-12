---
title: "Cant Install Docky"
date: 2010-05-22
forum: General Help
---

### Post by dewey_daniels on 2010-05-22
Well the title say it all. When I try to install from the Software center it gets to 3% it says > Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f OR in the details area it says > libdesktop-agnostic-vfs-gio libdesktop-agnostic-cfg-gconf libdesktop-agnostic-fdo-glib.So then I try it in terminal and get >  apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
derek@derek-laptop:~$ sudo apt-get install docky gnome-do-docklets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  docky: Depends: libgnomedesktop2.20-cil (>= 2.26.0) but it is not going to be installed
         Depends: libmono-getoptions2.0-cil (>= 1.0) but it is not going to be installed
         Depends: librsvg2-2.18-cil (>= 2.26.0) but it is not going to be installed
         Depends: libwnck2.20-cil (>= 2.26.0) but it is not going to be installed
         Depends: python-docky but it is not going to be installed
  gnome-do-docklets: Depends: gnome-do (>= 0.8.2) but it is not going to be installed
  libdesktop-agnostic-cfg-gconf: Depends: libdesktop-agnostic0 (= 0.3.90-0ubuntu1) but it is not going to be installed
  libdesktop-agnostic-fdo-glib: Depends: libdesktop-agnostic0 (= 0.3.90-0ubuntu1) but it is not going to be installed
  libdesktop-agnostic-vfs-gio: Depends: libdesktop-agnostic0 (= 0.3.90-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
.Any help is good.



PS I will bump untill it is solved

---

### Post by dewey_daniels on 2010-05-22
bump :(

---

### Post by Phrea on 2010-05-22
> **dewey_daniels said:**
> bump :(

> OP: 7 Minutes Ago

> PS I will bump untill it is solved

Not going to work like this, be a little patient.

---

### Post by dewey_daniels on 2010-05-22
On all my threads i try to be patient and on every thread they disappear.

---

### Post by ankspo71 on 2010-05-22
Hi,
hmm, I don't know what to make of that 3rd party error message, but I would try opening the terminal and pasting this command:

```
sudo apt-get install -f docky
```

PS. be sure all other package installers are closed first (Software Center, Synaptic Package Manager, Update Manager, etc)
Hope this helps.

---

### Post by dewey_daniels on 2010-05-22
> derek@derek-laptop:~$ sudo apt-get install -f docky
[sudo] password for derek: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  docky: Depends: libgnomedesktop2.20-cil (>= 2.26.0) but it is not going to be installed
         Depends: libmono-getoptions2.0-cil (>= 1.0) but it is not going to be installed
         Depends: librsvg2-2.18-cil (>= 2.26.0) but it is not going to be installed
         Depends: libwnck2.20-cil (>= 2.26.0) but it is not going to be installed
         Depends: python-docky but it is not going to be installed
  libdesktop-agnostic-cfg-gconf: Depends: libdesktop-agnostic0 (= 0.3.90-0ubuntu1) but it is not going to be installed
  libdesktop-agnostic-fdo-glib: Depends: libdesktop-agnostic0 (= 0.3.90-0ubuntu1) but it is not going to be installed
  libdesktop-agnostic-vfs-gio: Depends: libdesktop-agnostic0 (= 0.3.90-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
 nothing. Any other ideas

---

### Post by dewey_daniels on 2010-05-22
Solved 

Just installed from package manager
r

---

