---
title: "Printer"
date: 2010-01-15
forum: General Help
---

### Post by mikemikemike on 2010-01-15
According to my family the printer magically uninstalls itself from the system. I have never had an issue. According to my mom it happens whenever ubuntu updates.

What could be the cause of this?

I install it by

```
sudo apt-get install build-essential
wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
tar zxf foo2zjs.tar.gz
cd foo2zjs
sudo make uninstall
make
./getweb 1020
sudo make install install-hotplug cups
sudo gnome-cups-manager (won't work skip to next step)
sudo make cups
```

---

### Post by warfacegod on 2010-01-15
It could be disabling itself not actually uninstalling.

---

### Post by mikemikemike on 2010-01-15
It is not even listed under Printing when I check. As soon as I run the above commands its back and working.

---

### Post by mikemikemike on 2010-01-16
bump

---

