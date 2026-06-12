---
title: "Fixing Partitions on Ubuntu (Edubuntu) to Dual Boot with Windows"
date: 2006-05-15
forum: General Help
---

### Post by Aladnsane on 2006-05-15
So here's the deal - I'm a linux noob, so I installed incorrectly; I had winXP running on a 6gb partition, and attempted to make a 6gb partition to run linux off of, a 1.5gb or so for a swap partition, and the rest for Data. Something went a little haywire (ie I failed ;) and I ended up wiping the windows partition, getting linux on a 53gb partition, and a 2.14gb swap partition. (I'm very, very confused... but anyhow).

Is it possible for me to resize the bootpartition without just restarting from scratch?.. 

Restarting isn't the /end/ of the world, but this being a Vaio, it's a lot more complicated than it should be ;). Tips?..

---

### Post by empthollow on 2006-05-15
go to [http://www.ubuntu.com/download/](http://www.ubuntu.com/download/)
click your country, download the live cd, burn it
it will boot automatically as long as your bios is set to boot from cd
when the desktop starts up go to
applications -> system tools -> gparted
gparted will allow you to resize your partitions as well as delete and create partitions.

have fun

---

