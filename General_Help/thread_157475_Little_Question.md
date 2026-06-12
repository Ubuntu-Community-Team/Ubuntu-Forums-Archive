---
title: "Little Question"
date: 2006-04-09
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2006-04-09
When I want to mount my MP3 Player, I have to type: sudo mount -a    in terminal. Is there a way that the PC does it automatically and shows the contents of the player without me having to do a thing?

---

### Post by varunus on 2006-04-09
The computer should be mounting USB devices you plug in automatically; it seems like this is not happening for some reason.

What kind of mp3 player is it?  Also, can you post the contents of the file /etc/fstab here?

---

### Post by s_h_a_d_o_w_s on 2006-04-09
It's a Sony PSP.



Here's the fstab: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1 /home/max/PSP vfat iocharset=utf8,umask=000 0 0

---

