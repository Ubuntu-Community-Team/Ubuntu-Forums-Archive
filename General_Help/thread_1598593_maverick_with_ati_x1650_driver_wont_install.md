---
title: "maverick with ati x1650 driver wont install"
date: 2010-10-16
forum: General Help
---

### Post by buzzmandt on 2010-10-16
i need help on installing ati x1650 pro driver.  ubuntu hardware driver is not showing any driver for it and i tried to install it manually from ati linux driver and i'm getting errors.

```
buzzmandt@main:~/Downloads$ sudo sh ./ati-driver-installer-9-3-x86.x86_64.run 
[sudo] password for buzzmandt: 
Created directory fglrx-install.wYeDwa
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.35-22-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.wYeDwa
buzzmandt@main:~/Downloads$ 

```
```
02:00.0 VGA compatible controller: ATI Technologies Inc Radeon X1650 Pro (rev 9e)
```

---

### Post by buzzmandt on 2010-10-17
hmmm, ok,  maybe if i rephrase the question.

Trying to play ddo (dungeons and dragons online)  Getting an error saying that the game requires texturing and is complaining that the ati card with the open source drivers isn't doing it.  any suggestions?

---

### Post by Mark Phelps on 2010-10-17
Sorry, but there is no current AMD/ATI proprietary driver that works with Ubuntu versions since 8.10.  The only driver that works now is the open-source driver, and that is installed by default during system setup.

You're only alternative, if you want 3D acceleration sufficient for gaming, is to buy one of the newer cards that does have propietary driver support.

---

### Post by buzzmandt on 2010-10-17
thanks for the reply. kinda figured something about those lines but wanted to be sure.  guess i'll get an nvidia lol

---

