---
title: "can different desktops (ubuntu, edubuntu) run on one kernel?"
date: 2011-06-06
forum: General Help
---

### Post by dragonfly41 on 2011-06-06
On an old Acer Aspire 3610 notebook to be used by parent and children
I have installed a dual boot configuration with:-
/dev/sda1 - ntfs - Vista
/dev/sda2 - ext4 - Ubuntu 10.10 - mounted "/" 
/dev/sda3 - ext4 - Ubuntu 10.10 - mounted "/home"
/dev/sda4 - ntfs - data files accessible by Vista

What is the best way of adding Edubuntu desktop for children's use?

In one kernel can one user (parent) have Ubuntu 10.10 desktop and other users (children) have Edubuntu 10.10 desktop with parental controls?

i.e. can different desktops be configured to run for different users on one kernel?

Or is a triple boot installation necessary:

Vista, Ubuntu, Edubuntu?

I guess that I could reformat and use the partition /dev/sda4 for Edubuntu if necessary.

---

### Post by zvacet on 2011-06-07
You can install edubuntu with 

```
sudo apt-get install edubuntu-desktop
```

Both desktops will run on same kernel.You cab choose witch desktop you want to login on login screen>sessions.I don´t know about parental control.

---

### Post by jerrrys on 2011-06-07
i would go with triple boot, just to keep the kids off my working system.

---

### Post by linuxinstalledfromhdd on 2011-06-07
I would resize my existing partition with the installation disc, and provide the kids with their own system so they can't mess around with my own..

Good to see you are using 10.10.. If you need a guide for that:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

