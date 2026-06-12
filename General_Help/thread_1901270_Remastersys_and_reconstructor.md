---
title: "Remastersys and reconstructor"
date: 2011-12-28
forum: General Help
---

### Post by The Legend Mohammad on 2011-12-28
how I can install Remastersys and reconstructor on Ubuntu 11.10 amd64 version?
thank you

---

### Post by Basher101 on 2011-12-28
for remastersys just type in the terminal ```
sudo apt-get install remastersys
``` do the same for reconstructor. It may not be in the repositories so you may have to add it to your repos.

---

### Post by The Legend Mohammad on 2011-12-28
It doesn't work
It says "cannot found the package"

---

### Post by Basher101 on 2011-12-28
The Remastersys repository needs to be added to your /etc/apt/sources.list

Paste the following into the sources.list:
For Karmic, Lucid and Newer with grub2 - version 2.0.13-1 and up
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/


Then simply either reload in Synaptic or you can "sudo apt-get update" and install remastersys.

[COLOR="Red"]**_EDIT:Remastersys is also in the Software center. Just open the Software Center and type in the search box Remastersys, you will find it there._**
[/COLOR]
i can't find anything for reconstructor. Are you sure that software is not discontinued?

---

### Post by westie457 on 2011-12-28
reconstructor is here, [http://linux.softpedia.com/get/Utilities/Reconstructor-16806.shtml](http://linux.softpedia.com/get/Utilities/Reconstructor-16806.shtml)

---

### Post by The Legend Mohammad on 2011-12-30
doesnot work

---

