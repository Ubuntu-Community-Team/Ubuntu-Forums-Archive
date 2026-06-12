---
title: "GRUB4DOS menu.list problem"
date: 2010-01-30
forum: General Help
---

### Post by Al Fischer on 2010-01-30
I just finished an install with 4 OS's. DOS, XP, WIN7, and UBUNTU. They work fine no with problems. However, the menu entry to run memtest does not work, However on my other system it works. The failing system is an i7 and the working one is a Core Duo. Both have a lot of ram. The Ubuntu os was copied with GPARTED. So it is identical.The menu.lst was a copy/paste job and then the HDxx's modified as needed. Please take a look and tell me where I went wrong.[ATTACH]145453[/ATTACH] 

####################################################################################################
#  AL MODS START

title BOOT FREEDOS
root    (hd0,0)
unhide  (hd0,0) 
unhide  (hd0,1) 
unhide  (hd0,2) 
unhide  (hd0,3)
makeactive
savedefault
chainloader +1


title BOOT WINDOWS XP
unhide (hd0,3)
hide   (hd0,0)     Hide DOS
hide   (hd0,1)     #Hide UBUNTU
hide   (hd0,2)     #Hide WIN7
root   (hd0,3)
makeactive
savedefault
chainloader (hd0,3)/ntldr 


title BOOT WINDOWS 7  
unhide (hd0,2)
#hide  (hd0,0)      #Hide DOS
#hide   (hd0,1)     #Hide UBUNTU
#hide   (hd0,3)     #Hide XP
root   (hd0,2)
makeactive
savedefault
chainloader +1


title       Ubuntu 8.10, kernel 2.6.27-11-server
savedefault
root     (hd0,1)
kernel    /boot/vmlinuz-2.6.27-11-server root=/dev/sda2 ro quiet splash
initrd    /boot/initrd.img-2.6.27-11-server


title		Ubuntu 8.10, memtest86+
root            (hd0,1)
kernel		/boot/memtest86+.bin
quiet

#   AL MODS END
############################################################################################

THIS IS REALLY DRIVING ME NUTS!! What did I overlook??

---

### Post by running_rabbit07 on 2010-02-10
Got it fixed yet?

---

### Post by Bq32 on 2010-02-10
> **Al Fischer said:**
> I just finished an install with 4 OS's. DOS, XP, WIN7, and UBUNTU. They work fine no with problems. However, the menu entry to run memtest does not work, However on my other system it works. The failing system is an i7 and the working one is a Core Duo. Both have a lot of ram. The Ubuntu os was copied with GPARTED. So it is identical.The menu.lst was a copy/paste job and then the HDxx's modified as needed. Please take a look and tell me where I went wrong.[ATTACH]145453[/ATTACH] 

####################################################################################################
#  AL MODS START

title BOOT FREEDOS
root    (hd0,0)
unhide  (hd0,0) 
unhide  (hd0,1) 
unhide  (hd0,2) 
unhide  (hd0,3)
makeactive
savedefault
chainloader +1


title BOOT WINDOWS XP
unhide (hd0,3)
**hide   (hd0,0)     Hide DOS**
hide   (hd0,1)     #Hide UBUNTU
hide   (hd0,2)     #Hide WIN7
root   (hd0,3)
makeactive
savedefault
chainloader (hd0,3)/ntldr 


title BOOT WINDOWS 7  
unhide (hd0,2)
#hide  (hd0,0)      #Hide DOS
#hide   (hd0,1)     #Hide UBUNTU
#hide   (hd0,3)     #Hide XP
root   (hd0,2)
makeactive
savedefault
chainloader +1


title       Ubuntu 8.10, kernel 2.6.27-11-server
savedefault
root     (hd0,1)
kernel    /boot/vmlinuz-2.6.27-11-server root=/dev/sda2 ro quiet splash
initrd    /boot/initrd.img-2.6.27-11-server


title		Ubuntu 8.10, memtest86+
root            (hd0,1)
kernel		/boot/memtest86+.bin
quiet

#   AL MODS END
############################################################################################

THIS IS REALLY DRIVING ME NUTS!! What did I overlook??

What I bolded, did you mean to uncomment "Hide DOS"? That's all I see wrong, but GRUB4DOS is probably different from GRUB.

---

### Post by Al Fischer on 2010-02-10
The part you bolded is a typo. I guess I deleted the # by mistake!  (gotta learn to type)

The problem I have run into is with the **memtest** part. It works fine on one machine (IBM T61 Laptop) but will not go on the desktop (Asus P6T with i7 cpu). Both were from copies of an original partition so everything is the same.

The other 'title' sections work fine.

---

### Post by running_rabbit07 on 2010-02-10
Here is a copy of what my menu.list shows for the memtest entry. You may also want to check and make sure this file in the boot folder is there and that it didn't get messed up when it was copied. Maybe even try and recopy it from the working system to the broken system.

---

