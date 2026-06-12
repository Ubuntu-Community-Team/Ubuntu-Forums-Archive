---
title: "Ubuntu 11.04 Grub Customizer ignores splash image"
date: 2011-09-25
forum: General Help
---

### Post by hal8000 on 2011-09-25
I'm using Ubuntu 11.04 fully updated (with Gnome 2 desktop).

I've used grub cuustomizer and changed the splash screen placing an image called sunday.jpg in /boot/grub

However when reloading, grub has changed resolution to 1280x1024 but not loaded my splash screen and I dont know why.

Here are some info:
cat /etc/boot/grub/grub.cfg

--snip--
### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root a2ba6ede-06fd-4140-98c0-0fa2ed273d65
insmod jpeg
if background_image /boot/grub/sunday.jpg; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi



ls -l /boot/grub
-rwxr-xr-x 1 root root 590987 2011-09-25 13:42 /boot/grub/sunday.jpg

So my image is in the correct location, is loaded by grub.cfg but fails to display as a splash, anyone know why?

Permission of jpg are 755 does this make a difference?
The image is 1280x1024 24bit colour.
Thanks in advance

---

