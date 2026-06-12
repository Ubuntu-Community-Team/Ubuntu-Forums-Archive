---
title: "Unable to restore remastersys backup"
date: 2010-08-28
forum: General Help
---

### Post by sarin_cv on 2010-08-28
Hi all... I have created a remastersys backup using dist option. Now the issue is, while booting with the restore image, there is no option for restore. Both live and install menu option lead to live cd mode. I tried running ubuquity from terminal after booting in live mode also. Please help

---

### Post by JOHNNYG713 on 2010-08-28
boot to live desktop, go to system, Administration, Install release ! This should open the installer.

---

### Post by mike555 on 2010-08-28
-- from another post ---

You mast have ubiquity and ubiquity-frontend-gtk or ubiquity-frontend-kde installed, depending on your desktop environment. When you boot from remastersys backup dvd it really doesn't matter whether you chose install or run as LiveCd because both these options works the same. That is a bug of the install option of remastersys, I suppose . Anyway, after you run it go to menu -> administration (or wherever you have it) and chose install. It is the installer that you already know from installation livecd. It allows you to install your backup the same way as a clean liveCd.

---

### Post by deserthowler on 2010-08-28
Open Synaptic and check if the following programs are installed; ubiquity, ubiquity-frontend-debconf, ubiquity-ubuntu-artwork, ubiquity-casper and ubiquity-frontend-gtk..  Install any that are not installed.

Earl

---

### Post by sarin_cv on 2010-08-30
> **JOHNNYG713 said:**
> boot to live desktop, go to system, Administration, Install release ! This should open the installer.

There is no such option in system->Administration... :(

---

### Post by sarin_cv on 2010-08-30
> **deserthowler said:**
> Open Synaptic and check if the following programs are installed; ubiquity, ubiquity-frontend-debconf, ubiquity-ubuntu-artwork, ubiquity-casper and ubiquity-frontend-gtk..  Install any that are not installed.

Earl

Is this to be done before creatin the backup or after booting in to live CD?

---

### Post by sarin_cv on 2010-08-30
[bouncing post]

---

### Post by sarin_cv on 2010-08-30
[bouncing once again]

---

### Post by sarin_cv on 2010-09-01
Issue resolved... Installed ubiquity gtk and created a new backup using remastersys... Now the install option is coming in Live CD mode.... To my surprise,  Direct install option from the boot menu is also working...

---

