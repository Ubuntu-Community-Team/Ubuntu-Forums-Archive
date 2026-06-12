---
title: "i erase the partition of ubuntu :("
date: 2010-05-17
forum: General Help
---

### Post by osama2026 on 2010-05-17
i erase the partition of ubuntu by disk utility  in mac os
when i restart my laptop and select windows os partition but windows os not booting
and the screen show to me
 
error: no such partition.
grub rescue>






sorry to my english :(

---

### Post by ajgreeny on 2010-05-17
This is probably because grub was put on the mac equivalent of the MBR; I've never used a mac so have no idea about the boot sequence of those machines.  All the grub configuration files were on the ubuntu partition which has now been deleted, so no configuration is available, and you can not boot to anything.

You will need to restore either the windows bootloader to the MBR or set everything back to the mac style boot setup, but being a mac, I will have to leave it to others to tell you how in detail, or for you to do your own google search.

---

