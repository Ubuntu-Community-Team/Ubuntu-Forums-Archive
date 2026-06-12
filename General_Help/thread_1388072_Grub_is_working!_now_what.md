---
title: "Grub is working! now what???"
date: 2010-01-22
forum: General Help
---

### Post by Amdahl1 on 2010-01-22
Woo Hoo!!! my grub edit finally took! I guess it helps to know what version you are working with...:lolflag:

So I got my DOS 6.0 entry in... but Grub reports file not found.
I assume grub is fine, and DOS6 was working and I haven't done anything to it. Needless to say, I'm guessing that I'm telling grub to look in the wrong place for the dos bootloader. 

Here's what I have in my 40_Custom file:
#!/bin/sh
exec tail -n +3 $0 
menuentry "MS-DOS 6.0" {
insmod chain
insmod vfat
search --fs-uuid --set 3c34-9666
chainloader +1
}

The "vfat" and uuid of "3c34-9666" were reported by using sudo blkid
Do I need to set the root? I thought the uuid took care of that?:confused:

---

### Post by adam814 on 2010-01-22
I don't know if it's strictly needed, but looking at the entry for my Vista install after the "insmod ntfs" line I have a "set root=(hd0,2)" line where my Vista partition is on /dev/sda2.  Vista works alright, although I have to say I don't know how the DOS bootloader itself works.

---

### Post by Amdahl1 on 2010-01-22
I'll add the set root command and see what happens... Wish me luck!

---

### Post by Amdahl1 on 2010-01-22
Didn't help. I'm going to try and re-install DOS on it's partition in case something got wiped...

That didn't do it either. ??? I think I need to start looking for more info.

---

### Post by Leppie on 2010-01-22
i think i've read somewhere that dos cannot be booted from grub2.

---

