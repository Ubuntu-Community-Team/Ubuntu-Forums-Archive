---
title: "system broke"
date: 2006-07-01
forum: General Help
---

### Post by hopspitfire on 2006-07-01
I was "trying" to install wesnoth by following the instructions here: [http://www.wesnoth.org/wiki/WesnothBinariesLinux](http://www.wesnoth.org/wiki/WesnothBinariesLinux)

apparently, after adding the sources:

```
deb http://ftp.tr.debian.org/debian/ unstable main
deb-src http://ftp.tr.debian.org/debian/ unstable main
```

and typing sudo apt-get install wesnoth i continued reading that page and it said 

> "Do not attempt to install the debian package and associated dependencies using dpkg as you will break your environment!"

now, whenever i try to install or remove anything, it adds EVERY package on my system to the remove list. I removed the sources, and when I go to Synaptic Pkg Manager, it says there are 2 broken packages, and when i look for them in the filters, it just shows all the packages. Upon opening the update manager, this is what pops up

"Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

i ran "sudo apt-get install -f", this is what pops up

```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-15 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

im stumped....does anyone have any ideas?

---

### Post by hopspitfire on 2006-07-01
bump

---

### Post by nomail on 2006-07-01
Try this one [http://ubuntuforums.org/showthread.php?t=191741&highlight=tzdata]("http://ubuntuforums.org/showthread.php?t=191741&highlight=tzdata")

---

### Post by hopspitfire on 2006-07-01
thank you, its fixed

---

