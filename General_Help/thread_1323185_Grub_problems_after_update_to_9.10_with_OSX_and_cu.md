---
title: "Grub problems after update to 9.10 with OSX and custom boot options"
date: 2009-11-11
forum: General Help
---

### Post by dooglex on 2009-11-11
Hi,
I used to boot OSX using menu.lst which looked like this:
title		OSX
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1

now i have done a clean install of 9.10 which finds the osx partition but when i boot it get only the attached screenshot of output, and then nothing.
Im not 100% sure that its not grub crashing and not the osx bootloader, but if grub has handed over then this belongs on an OSX forum instead sorry! I will close and move it.

I tried to add a custom entry in 40_custom then adding +x priveledges and then running update grub2 and the grub.cfg shows the new entry but on boot no new options appear so I cant test adding my own options! 

So in summary does anyone know why my custom created entry in 40_custom doesn't even appear let alone work? (attached at end) or for full marks why grub2 wont natively boot osx! 

thanks

menuentry "OSX try 2" {
set root=(hd0,3)
insmod video
insmod vbe
gfxmode="1280x800x32"
xnu_kernel /mach_kernel rd=disk0s6
if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
   xnu_mkext /System/Library/Extensions.mkext
else
   xnu_kextdir /System/Library/Extensions
fi
}

---

