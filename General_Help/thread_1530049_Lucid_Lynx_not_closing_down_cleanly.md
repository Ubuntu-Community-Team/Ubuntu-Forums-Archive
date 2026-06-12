---
title: "Lucid Lynx not closing down cleanly"
date: 2010-07-13
forum: General Help
---

### Post by Gael33 on 2010-07-13
For the last couple of days my pc is refusing to close down. I have not installed any new software or downloaded any upgrades. I click on the close button in the right hand corner of my screen, and then click on closedown in the little window that appears ... and nothing happens. Does anyone know how I can fix this?

Thanks,

gael.

---

### Post by lordskid on 2010-07-13
This happens to me too. it hangs (4 out of 5 times) after the message the system will now halt... 

I read somewhere it is due to some splash screen error...
so I changed the quiet splash option from /etc/default/grub file

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" => GRUB_CMDLINE_LINUX_DEFAULT=""

and did a sudo update-grub

it still happens but less frequent (approximately 1 out of 10 shutdowns)

---

