---
title: "Install Multiple/Different Distros"
date: 2010-07-15
forum: General Help
---

### Post by losl on 2010-07-15
How could i use Wubi to install multiple/different distros in one PC?

After installing one distro and re-launching Wubi for install the 2nd one
requires to uninstall the first one. Is it possible to stop the uninstall routine ?  

Thank you !!

---

### Post by AceRoom on 2010-07-15
Instead of using Wubi, why don't you try using a LiveCD or LiveUSB. That should work. I used to have Mint and Ubuntu installed at the same time. If you don't want to burn the ISO to a CD, open up the STARTUPDISK Creator from your already installed distro and use it to create a LiveUSB.

Once booted into the Live Environment, you can repartition the hard disk and create a new partition to install your new distro on it. This will keep the old distros and even Windows alive as long as you don't delete the partitions they're on.

Word of warning, before you mess around with resizing partitions, you might want to backup your data. Sometimes, things do go wrong.

---

