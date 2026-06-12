---
title: "Cannot boot from live CD with ubuntu installed"
date: 2011-02-20
forum: General Help
---

### Post by Uthallan on 2011-02-20
Hello,

 I have Ubuntu 10.10 fully installed on my laptop, I am trying to get my main drive partitioned so I can install windows as well, only problem is that I can't do that without using my live CD to unmount the drive. Heres the big problem, my CD just wont boot. when I try to boot from it nothing happens and my computer just starts up as normal as if there was no CD in the first place. I have set my CD drive as my main boot device in BIOS so I know thats not the problem, and I have also tried using an external USB drive to boot from with the same results. I used the same drives and CD to do the install just a few days ago so I'm fairly certain that they are not the problem. The only thing that I can think of that might be causing trouble is that when I installed I got a black screen on my first boot (caused by my nvidia drivers apparently)and had to edit my GRUB a little to fix it. 

  So does anyone know why I can boot from my CD?

For reference This is what my GRUB looks like right now:

recordfail
insmod part-msdos
insmod ext2
set root='(hdo,msdos1)'
Search --no-floppy --fs-uuid --set 329b8dbf-d45f-4b51-bff9-3b661a45d\
f46
linux  /boot/vmlinuz-2.6.35-25-generic root=UUID=329b8dbf-d45f-4b51-b\
ff9-3b661a45df46  ro  quiet splash
initrd /boot/initrd.img-2.6.35-25-generic

---

### Post by Foxheadz on 2011-02-20
is there any button at startup like f11 that opens a boot selection menu?

---

### Post by Uthallan on 2011-02-20
yes there is, and I have tried to select my CD drive from that menu but I get the same results...nothing

---

### Post by Uthallan on 2011-02-20
bump?

---

### Post by Uthallan on 2011-02-22
Maybe someone could tell me how to reset my GRUB back to it's original state so I can see if it fixes my problem?

---

