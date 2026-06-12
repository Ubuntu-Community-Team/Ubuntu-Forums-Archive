---
title: "virtualbox kernel error"
date: 2011-08-20
forum: General Help
---

### Post by fidelandche on 2011-08-20
Hi all,

Tried to open VB to run one of the programmes I need XP for but I got the following error messages, so not really sure on what to do

---

### Post by ofnuts on 2011-08-20
> **fidelandche said:**
> Hi all,

Tried to open VB to run one of the programmes I need XP for but I got the following error messages, so not really sure on what to do

1) make sure you have the vbox-ose-dkms and dkms packages installed

2) check that you have 
```
/lib/modules/2.6.32-34-generic-pae/updates/dkms/vboxdrv.ko
```
(replace the kernel name by the one you run, you should have one such file per kernel if you have several kernels). 

There is a "virtualization" section on Ubuntu forums ([http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)) where you can get more expert answers. There is also forums.virtualbox.org

---

### Post by Old_Grey_Wolf on 2011-08-20
> **fidelandche said:**
> Hi all,

Tried to open VB to run one of the programmes I need XP for but I got the following error messages, so not really sure on what to do

It appears from the screenshot that you didn't run the command that Virtualbox instructed you to run as root. Use ```
sudo /etc/init.d/vboxdrv setup
```

ofnuts also gave instructions for dkms which you also need as mentioned in the Virtualbox instructions in the pop-up window. If you have been using Ubuntu since 2009, you probably have it installed.

---

### Post by fidelandche on 2011-08-21
Thanks ofnuts for the helpful post and for pointing me in the right direction for the "virtualization" section.

Old_Grey_Wolf, thanks for pointing the bit where I missed "sudo" that's where I was going wrong:oops:

All working now, so all that's great.

Cheers

---

