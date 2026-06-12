---
title: "Unable to install Java."
date: 2006-06-08
forum: General Help
---

### Post by YourSurrogateGod on 2006-06-08
The command-line says it all.
```
ysg@ysg-desktop:~$ sudo apt-get -f install sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree... Done
sun-java5-plugin is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java5-jre: Depends: sun-java5-bin (= 1.5.0-06-1) but it is not going to be installed or
                          ia32-sun-java5-bin (= 1.5.0-06-1) but it is not installable
  sun-java5-plugin: Depends: sun-java5-bin (= 1.5.0-06-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
ysg@ysg-desktop:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree... Done
sun-java5-plugin is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java5-jre: Depends: sun-java5-bin (= 1.5.0-06-1) but it is not going to be installed or
                          ia32-sun-java5-bin (= 1.5.0-06-1) but it is not installable
  sun-java5-plugin: Depends: sun-java5-bin (= 1.5.0-06-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
Why am I getting those errors at the bottom?

---

### Post by YourSurrogateGod on 2006-06-08
Ok, it seems to have installed fine after using the GUI to do it... odd.

---

### Post by asimon on 2006-06-08
There must have been something wrong with the dependencies of sun-java5-bin, which it did not wanted to install.

I dunno if that may have fixed your issue but you could have tried what apt-get recommended you to do. Running just 'apt-get -f install' instead of 'apt-get -f install sun-java5-jre sun-java5-plugin'.

---

### Post by YourSurrogateGod on 2006-06-08
[QUOTE=asimon]There must have been something wrong with the dependencies of sun-java5-bin, which it did not wanted to install.

I dunno if that may have fixed your issue but you could have tried what apt-get recommended you to do. Running just 'apt-get -f install' instead of 'apt-get -f install sun-java5-jre sun-java5-plugin'.[/QUOTE]
I have, but to no avail. Oh well, it seems to have worked now after I did it with the GUI.

---

