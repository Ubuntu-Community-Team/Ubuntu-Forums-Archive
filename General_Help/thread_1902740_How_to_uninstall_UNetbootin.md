---
title: "How to uninstall UNetbootin"
date: 2011-12-31
forum: General Help
---

### Post by tejli007 on 2011-12-31
Hi all really need your help.

How can i uninstall 
**UNetbootin**

? any command?
anyway can i install a dos for ubuntu?not grob.


thanks for helping

---

### Post by BC59 on 2011-12-31
Should be something like 
sudo apt-get remove unetbootin
or check your Ubuntu Software Center if there is an entry to remove.

---

### Post by tejli007 on 2011-12-31
> **BC59 said:**
> Should be something like 
sudo apt-get remove unetbootin
or check your Ubuntu Software Center if there is an entry to remove.

thanks for replay sir

when i type your command it says:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package unetbootin is not installed, so not removed
The following package was automatically installed and is no longer required:
  unetbootin-translations
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

in ubuntu software manager got button just for install

what should i do?

---

### Post by BC59 on 2011-12-31
> **tejli007 said:**
> thanks for replay sir

when i type your command it says:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package unetbootin is not installed, so not removed
The following package was automatically installed and is no longer required:
  unetbootin-translations
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

in ubuntu software manager got button just for install

what should i do?

Well follow the instructions and run:

sudo apt-get autoremove unetbootin-translations

or just  

sudo apt-get autoremove

---

### Post by tejli007 on 2011-12-31
> **BC59 said:**
> Well follow the instructions and run:

sudo apt-get autoremove unetbootin-translations

or just  

sudo apt-get autoremove

is still there sir when i try to boot from USB.

nvm

any chance to boot my windows iso without USB and CD?or to run the windows setup.exe so i can make dual boot?

---

