---
title: "Grub Install question"
date: 2006-02-18
forum: General Help
---

### Post by jenkins_t on 2006-02-18
I have a dual boot laptop w/ XP and Mepis 3.4. Grub is my bootloader. My /boot/grub/menu.lst is as follows (this is of course in my Mepis /boot/grub).

```

timeout 15
color cyan/blue white/blue
foreground ffffff
background 0639a1

gfxmenu /boot/grub/message

default 1

title Mepis Linux 3.4
kernel /boot/vmlinuz-2.6.15-1-586tsc root=/dev/hda2 nomce quiet vga=791 

title Windows_XP
rootnoverify (hd0,0)
chainloader +1

title MEMTEST
kernel /boot/memtest86.bin

```

If I install Ubuntu to free space on hda and leave MBR as is, how would I tell this file where to look for Ubuntu?

My Ubuntu hda will be hda8 for / and hda9 for/home. 

I think that I can use same swap, hda6, is that right (swap)?

---

### Post by TimeGoneBomb on 2006-02-18
You just need to run the installer, thats it! The Ubuntu installer will set up grub for you, and it should have all 3 operating systems listed. Worked for me. The only thing that happened is that it changed the boot menu to text mode when it was graphics mode before I installed ubuntu.

And yes, you only need one swap partition on the computer. All distros will use it.

---

### Post by jenkins_t on 2006-02-18
What if I want to keep boot menu like it is? I dont wanna change it b/c my family has just gotten use to it being this way...:)

[QUOTE=TimeGoneBomb]You just need to run the installer, thats it! The Ubuntu installer will set up grub for you, and it should have all 3 operating systems listed. Worked for me. The only thing that happened is that it changed the boot menu to text mode when it was graphics mode before I installed ubuntu.

And yes, you only need one swap partition on the computer. All distros will use it.[/QUOTE]

---

