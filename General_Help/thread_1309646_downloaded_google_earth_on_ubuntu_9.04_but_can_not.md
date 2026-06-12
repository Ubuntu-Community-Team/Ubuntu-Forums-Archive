---
title: "downloaded google earth on ubuntu 9.04 but can not open it"
date: 2009-11-01
forum: General Help
---

### Post by savvavas on 2009-11-01
When I tried to open googleearthlinux.bin I get a message "There is no installed viewer capable of displaying the document.". What do I do??

---

### Post by mikewhatever on 2009-11-01
Well, you are not supposed to open it. If you want to install GE, use this guide or google for another one.
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by realzippy on 2009-11-01
Maybe better to install it by using medibuntus repository.Open terminal,type:

[B]sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update[/B]

After this you can install googleearth through synaptic packet manager.

---

### Post by emoguitarist06 on 2009-11-01
> **savvavas said:**
> When I tried to open googleearthlinux.bin I get a message "There is no installed viewer capable of displaying the document.". What do I do??

right click the GoogleEarthLinux.bin and under permissions check the box that says "allow executing as a program" and close.

open terminal
go to the folder that contains the file
(so for me it was "cd Downloads")
and install with this code
"sudo ./GoogleEarthLinux.bin"

---

