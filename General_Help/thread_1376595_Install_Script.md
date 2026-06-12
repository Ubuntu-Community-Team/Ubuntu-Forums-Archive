---
title: "Install Script"
date: 2010-01-09
forum: General Help
---

### Post by mikemikemike on 2010-01-09
Can anyone write me a script that automatically executes the following items in sequential order?

```
sudo apt-get install build-essential
wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
tar zxf foo2zjs.tar.gz
cd foo2zjs
sudo make uninstall
make
./getweb 1020
sudo make install install-hotplug cups
sudo make cups
```My printer randomly uninstalls it self somehow, according to my mom who I am sure screws something up. So I just want to be able to install it a little quicker by having a file to double click

---

### Post by iponeverything on 2010-01-09
> **mikemikemike said:**
> Can anyone write me a script that automatically executes the following items in sequential order?

```
sudo apt-get install build-essential
wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
tar zxf foo2zjs.tar.gz
cd foo2zjs
sudo make uninstall
make
./getweb 1020
sudo make install install-hotplug cups
sudo make cups
```
My printer randomly uninstalls it self somehow, according to my mom who I am sure screws something up. So I just want to be able to install it a little quicker by having a file to double click

```
#!/bin/bash
sudo apt-get install build-essential
wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
tar zxf foo2zjs.tar.gz
cd foo2zjs
sudo make uninstall
make
./getweb 1020
sudo make install install-hotplug cups
sudo make cups
```

save it to a file and do "chmod 755" to it.

---

### Post by mikemikemike on 2010-01-09
double post sorry.

---

