---
title: "Can't find Windows in Grub"
date: 2009-10-06
forum: General Help
---

### Post by WeTakeItAll on 2009-10-06
Hi.. I just installed Ubuntu today.. and when I went to restart and boot back into Vista it just automatically boots into Ubuntu.

When I went back into the Grub menu I notice Vista isn't there anymore :/

I'm a real newb when it comes to linux so any help would be greatly appreciated.

---

### Post by lindsay7 on 2009-10-06
Post the result of typing 

sudo fdisk -l  (lower case letter L) in the terminal

and also post 

cat /boot/grub/menu.lst  (lower case L)

---

### Post by fluffman86 on 2009-10-06
Did you do a side-by-side installation of Ubuntu after booting from the live cd?  Are you sure you didn't accidentally erase Vista?

Also, when grub starts, do you get a message for just a few seconds that says to press Esc to view the boot list?  Or can you see several boot options like Ubuntu, Ubuntu (recovery mode), Memtest86+?

---

### Post by WeTakeItAll on 2009-10-06
> **lindsay7 said:**
> Post the result of typing 

sudo fdisk -l  (lower case letter L) in the terminal

and also post 

cat /boot/grub/menu.lst  (lower case L)


Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12158    97659103+  83  Linux
/dev/sda2           12159       13374     9767520    5  Extended
/dev/sda5           12159       13374     9767488+  82  Linux swap / Solaris



cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.


title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        34d03a73-f68d-416f-a5a2-1bde6971f4f4
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=34d03a73-f68d-416f-a5a2-1bde6971f4f4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        34d03a73-f68d-416f-a5a2-1bde6971f4f4
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=34d03a73-f68d-416f-a5a2-1bde6971f4f4 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        34d03a73-f68d-416f-a5a2-1bde6971f4f4
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=34d03a73-f68d-416f-a5a2-1bde6971f4f4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        34d03a73-f68d-416f-a5a2-1bde6971f4f4
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=34d03a73-f68d-416f-a5a2-1bde6971f4f4 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        34d03a73-f68d-416f-a5a2-1bde6971f4f4
kernel        /boot/memtest86+.bin
quiet

---

### Post by WeTakeItAll on 2009-10-06
> **fluffman86 said:**
> Did you do a side-by-side installation of Ubuntu after booting from the live cd?  Are you sure you didn't accidentally erase Vista?

Also, when grub starts, do you get a message for just a few seconds that says to press Esc to view the boot list?  Or can you see several boot options like Ubuntu, Ubuntu (recovery mode), Memtest86+?


I'm pretty sure I didn't accidently erase it. I probably did though haha.. thank god it was a fresh install and I had nothing on it.

And yeah I get the message for a few seconds that says to press Esc..

---

### Post by fluffman86 on 2009-10-06
looks like you wiped vista in the process of installing.  did you tell ubuntu to use the whole drive?

---

### Post by WeTakeItAll on 2009-10-06
Damn.. nah I didn't.. there is only like 90 odd gig available.. and it's a 500gig HDD

---

### Post by lindsay7 on 2009-10-06
fdisk shows one hard drive and if this is correct, there is no windows installation on this computer. You should install windows first as this is the best way for a dual boot installation to work.


Here is a step by step guide,

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by WeTakeItAll on 2009-10-06
I had Vista installed first, but must have fuzzed it up when installing Ubuntu and wiped Vista.. thanks for the information guys.

---

