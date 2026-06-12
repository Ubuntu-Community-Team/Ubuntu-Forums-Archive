---
title: "tricky grub/ntldr question"
date: 2009-07-14
forum: General Help
---

### Post by TheCrap on 2009-07-14
hi there. i'm running win xp(using ntldr) and ubuntu(grub) on different sata hdds. for installing ubuntu i removed my xp hdd for protection and now im using the bios bootmenu to choose between the two os. for the case one mbr crashes i wanted to create a crossconnection between both bootloader. so i entered windows into the menu.lst(with map (hd0)(hd1)...), copied the mbr from the ubuntu hdd to the win hdd and entered ubuntu to the boot.ini. for booting win from grub all is fine, but  ntldr only shows GRUB an a blinking cursor(i think its because grub now searches on the windows hdd, because if i first load grub an choose to load win(swap of hdds) and then in ntldr i choose to load ubuntu it works). is it possible to tell grub, if it finds itself on hd1 to do map (hd1)(hd0) map (hd0) (hd1) first befor the booting goes on?    TheCrap

---

