---
title: "how to  write cdfs Configuration  into /etc/modules ?"
date: 2010-04-04
forum: General Help
---

### Post by luofeiyu on 2010-04-04
i have installed cdfs 2.6 in my ubuntu9.1:
sudo apt-get install cdfs-src
sudo tar -xvf cdfs.tar.bz2
sudo make
sudo make install
how to  write cdfs Configuration  into /etc/modules ?
when i use command :
sudo gedit /etc/modules
to open the /etc/modules file,and then how to write??

---

### Post by cariboo on 2010-04-04
There is no /etc/modules file. You have to create a configuration file in /etc/modprobe.d eg: cdfs.conf

---

### Post by luofeiyu on 2010-04-07
sudo gedit /etc/modprobe.d/cdfs.conf
in the file: /cdfs.conf

what did i write?

---

