---
title: "How can install K3b version 0.12.13?"
date: 2006-03-05
forum: General Help
---

### Post by risknothin on 2006-03-05
I have K3b version 0.12.7, how can i update it to the newest version?  the website gives me instructions and then when i get to the part where it say to type "make" into the terminal nothing happeneds i get this error

make: *** No targets specified and no makefile found.  Stop.

so does anyone know how fix this?

---

### Post by Ramses de Norre on 2006-03-05
You probably don't have all the needed -dev files.
Run this in the directory of the source:```
sudo -s
apt-get install auto-apt
auto-apt update
auto-apt updatedb
auto-apt update-local
auto-apt run ./configure
./configure
apt-get install checkinstall
checkinstall -D make install

```
Should do the trick.
Some of the commands may take a while.

---

### Post by risknothin on 2006-03-05
what is auto apt?

---

### Post by risknothin on 2006-03-05
i did all that and then started K3b and its still version 0.12.7


What did i do wrong?

---

### Post by Ramses de Norre on 2006-03-05
You ran it in the directory of the source and you had no error messages? Then it should be installed.. You can check it with synaptic, when you open it scroll to the bottom of the list to the left. Their should be "checkinstall" which shows all the programs installed by checkinstall.
When it's in there: maybe you need another command to use the new k3b (find /usr/bin k3b).
Otherwise: install the .deb made by checkinstall (sudo dpkg -i file.deb) I think it's in the source directory by default.

@ risknothin: auto-apt is a program that makes it possible to auto install missing dependencies detected by ./configure, it can the same by other commands too.

---

