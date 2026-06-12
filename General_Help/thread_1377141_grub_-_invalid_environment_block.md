---
title: "grub - invalid environment block"
date: 2010-01-09
forum: General Help
---

### Post by slush puppie on 2010-01-09
after a forced shut down (booted to blank screen, nothing seemed to be happening) i get the "invalid environment block" error when choosing an OS in grub (v1.87~beta4). 

i've found posts that say to press 'e' and remove the "save_env recordfail" line and press ctrl+x, however when i press 'e' my screen doesn't show this exact line, it shows: 

recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
saved_entry=${chosen}
save_env saved_entry
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set edb1fb9f-1334-4121-9a10-b7bf5ff0d701
linux /boot/vmlinuz-2.6.31-16-generic root=UUID=edb1fb9f-1334-4121-9a10-b7bf5ff0d701 ro   quiet splash
initrd /boot/initrd.img-2.6.31-16-generic

i hope i got that all correct (obviously had to retype it onto another computer)... which line would i remove? would it be the "save_env recordfail" part of the 2nd line? 

or any other advice on how to get back into my system?!?! thanks so much.

---

