---
title: "Restoring old system from tar file on top of live system"
date: 2009-08-13
forum: General Help
---

### Post by and.hunt on 2009-08-13
I recently upgraded my laptop from 8.04 to 9.04, which has resulted in no end of problems (no connection to WPA networks etc.) and would like to downgrade back to 8.04. I have full backups on an external hd in the form of tar files which I would like to revert to, with separate root and home files (since there are separate root & home partitions on the laptop). The laptop can only be booted from the hard disk (no cd, no usb, no network possible). The hard disk also uses a proprietary Toshiba connector (it's an ancient IDE 1.8" hd), meaning I can't plug it in to an external pc. I only have one linux installation, beside a windows installation. What I'd like to know is how to revert the root partition to the backup I have (the home partition can be easily done by having console only, and logging in as root). I would preferably like to erase everything on the root partition, but this means I don't have a useable system (except for windows, which doesn't count) to extract the backup with. Is there any way of extracting the backup with a live system? The preferable method would be to load the whole os into ram, like in the case of DSL, which would free the disk for cleaning. I.e. does anyone know how to setup a DSL image as a file on a partition, and then configure GRUB to boot this file? Ideally this could be placed on the windows (NTFS) parition, to ensure a fully operating linux system that can be used to configure things as needed.

//Edit: I have, after some fiddling, managed to tease another partition onto the hard disk, which means I can add a spare installation installed via Ubuntu, essentially solving my problems.

//Edit: Problem solved: I managed to install puppy linux onto my windows partition, meaning I can easily deal with anything I need to on the other partitions.

---

