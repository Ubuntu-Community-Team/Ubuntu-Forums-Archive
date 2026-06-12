---
title: "Server-style boot entries in Grub2"
date: 2010-11-01
forum: General Help
---

### Post by cloud2dream on 2010-11-01
Hi

I've been searching all over the net and these forums all day and I can't find an answer that fits my situation, so here goes:

I've got karmic installed (as well as some other stuff), and i wanted to add an option to grub2 that boots into the command line without gdm starting (like pressing ctrl+alt+f1). I still want to have the normal graphical boot option available in Grub as well.

I've tried the recovery mode but that brings up an additional menu, I just want to go straight to the command line.

Does anyone know if this is possible?

Thanks
James

---

### Post by lordskid on 2010-11-04
If I understand you right then just add a menuentry to your /etc/grub.d/40_custom

after adding the custom menu entry do a sudo update-grub

a good example would be this. If you have a standard install of ubuntu it will create a link to the latest kernel to the root directory '/' without the version number. So this should work.

```

menuentry 'Ubuntu - Generic Text Mode' --class ubuntu --class gnu-linux --class gnu --class os {
	insmod ext2
	set root='(hd0,6)' #change this depending on your partition
	linux	/vmlinuz root=(hd0,6) quiet splash text 
        #don't forget to match partition to the one on top    
	initrd	/initrd.img
}

```

---

