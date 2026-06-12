---
title: "need to load scsi_mod kernel module"
date: 2010-09-02
forum: General Help
---

### Post by walterBE on 2010-09-02
xubuntu 9.10
Drobo 2gen

Hi,

I have a Drobo, sort of RAID storage device. It makes use of volumes of 2TB. Only the first volume (LUN) is shown up. According this information;
[http://drobo-utils.sourceforge.net/#only-one-lun-shows-up]("http://drobo-utils.sourceforge.net/#only-one-lun-shows-up")

... that happens if the scsi_mod kernel module is not loaded.

When I give the command ```
lsmod
``` I get a lot of loaded modules but not scsi_mod.

I have attempted to load that module but have no succes. Can anyone help me out please?

Greetings,
Walter

---

### Post by walterBE on 2010-09-04
Nevermind, problem solved. 

Of the scsi_mod module is present or not it seems to work now.

---

