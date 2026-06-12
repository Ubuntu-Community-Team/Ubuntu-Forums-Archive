---
title: "bootloader WTF"
date: 2006-03-04
forum: General Help
---

### Post by SVFUSiON on 2006-03-04
When I installed Ubuntu I install LiLO because GRUB wouldn't work, when my computer boots that drive it goes to lilo then stright to ubuntu. Windows Vista is also on this hardrive. Is there a way to fix this? I would really like to scap lilo and start with GRUB but I will taking anything working. 
Thanks!

---

### Post by akiro.yamamoto on 2006-03-04
Boot to ubuntu and add a windows entry to lilo's configuration file. I think it's in 
/etc/lilo.conf
It's been quite a while since I last used lilo so I'm a little rusty.
But the file should have examples for what you need to do.
When your through making changes.
Invoke lilo with
sudo lilo  (I think)
Anyway check 
info lilo
for more info.

---

