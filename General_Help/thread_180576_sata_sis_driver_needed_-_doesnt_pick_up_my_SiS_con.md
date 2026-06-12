---
title: "sata_sis driver needed - doesnt pick up my SiS controller"
date: 2006-05-22
forum: General Help
---

### Post by nic886 on 2006-05-22
when i put the ubuntu disk in to install it onto my new system, it does not pick up my hard disk drivers, only my USB key if it is plugged in. The same happens with knoppix but fedora core 5 picks up and works fine with it as sata_sis. is there a way i can install this driver so i can install and use ubuntu. i tried modprobe sata_sis but the module was not found. i have no floppy drive so i cant load anything from a floppy. ive tried googleing for help on my problem but ](*,) ive found nothing. does anyone know how to load this?

---

### Post by skippy81 on 2006-05-22
The easiest thing would just be to install DapperDrake.  I have an SIS ide controller which wasn't supported in Breezy but runs great in Dapper.

Dapper is only a week or so from release anyway so its not *really* a beta :p

---

### Post by nic886 on 2006-05-22
thanks i think that is the way it will b. i know this is a ubuntu forum but i need to resize my partitions using knoppix and qtparted 2 install but knoppix cant work with my sata_sis either is there a deb for this driver or can i resize the partitions from dapper install?

---

