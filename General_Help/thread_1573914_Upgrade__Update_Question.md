---
title: "Upgrade / Update Question"
date: 2010-09-13
forum: General Help
---

### Post by merlin_ie on 2010-09-13
Hey everyone. I've successfully managed to downgrade my gdm to 2.20 and get back using the custom logins I made, but when I do **sudo apt-get upgrade** from terminal, it overwrites the old gdm and things become messy. Is there any way to prevent the GDM being upgraded? I have 214 updates available (due to fresh Lucid install) but I don't want to install any packages until I can get this issue resolved

EDIT : looking at Update Manager, there is no mention of GDM packages.

---

### Post by TitanusEramius on 2010-09-13
Well, I can only give you a generel direction.
In Syaptic you mark the packages you don't want apt to upgrade, and then go to the menu Package > Lock Version.

As for GDM, I think it is a colloection of packages that makes up GDM in Ubuntu, so I can't really help you there since i don't wich.

Good luck

---

### Post by merlin_ie on 2010-09-14
> **TitanusEramius said:**
> Well, I can only give you a generel direction.
In Syaptic you mark the packages you don't want apt to upgrade, and then go to the menu Package > Lock Version.

As for GDM, I think it is a colloection of packages that makes up GDM in Ubuntu, so I can't really help you there since i don't wich.

Good luck

Thanks for reply. I did the upgrde this morning and installed the gdm-2.20 deb that i had saved on hard drive afterwards like so : 
```
sudo apt-get remove gdm
(**Installed deb i had**)
cd /usr
sudo mkdir X11R6
cd X11R6
sudo ln -s /usr/bin bin
```

---

### Post by emarkay on 2010-10-05
Ah, the old "Update", or is it "Upgrade", thing again... :) 
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/445654](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/445654)

Also be advised that "Lock Version" is ignored if using commands in "Recovery Consiole": [https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/452222](https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/452222)
Subscribe to these if interested in seeing any workarounds.

---

