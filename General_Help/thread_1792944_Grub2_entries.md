---
title: "Grub2 entries"
date: 2011-06-28
forum: General Help
---

### Post by rostom_zer on 2011-06-28
Hi every one.

I'm in 10.10 maverick with Grub2

now each time my OS upgrades the kernel, the old ones seems to be not removed

for example: now my OS upgraded to 2.6.35-30-generic

after rebooting, i found a new entry " ubuntu with linux kernel blablabla 2.6.35-30-generic "

and the older ones too " ubuntu with linux kernel 2.6.35-28-generic "

and " ubuntu with linux kernel 2.6.35-22-generic "

and windows 7 of corse as i installed it in a separated partition

when i visited the folder /boot/

here is what i have:
----------------------------------------------------------
rostom@ACER:/boot$ ls
grub (folder)                          

abi-2.6.35-22-generic
abi-2.6.35-28-generic         
abi-2.6.35-30-generic       

System.map-2.6.35-22-generic  
System.map-2.6.35-28-generic
System.map-2.6.35-30-generic

config-2.6.35-22-generic      
config-2.6.35-28-generic      
config-2.6.35-30-generic      

vmcoreinfo-2.6.35-22-generic
vmcoreinfo-2.6.35-28-generic
vmcoreinfo-2.6.35-30-generic

initrd.img-2.6.35-22-generic  
initrd.img-2.6.35-28-generic
initrd.img-2.6.35-30-generic  
  
vmlinuz-2.6.35-22-generic
vmlinuz-2.6.35-28-generic
vmlinuz-2.6.35-30-generic

memtest86+.bin
memtest86+_multiboot.bin
----------------------------------------------------------

now what should i do to remove these intries from my Grub2 list and thier apropriate files if possible

i think it's all comes from this folder, no ?

help please 

thanX in advance

best regards, rostom

---

### Post by Ozymandias_117 on 2011-06-28
If you're certain the newer kernels are working fine, you can remove the older ones in Synaptic Package Manager.  Once they've been removed from your system, it will automatically update your grub entries.

---

### Post by oldfred on 2011-06-28
Ozymandias_117 is correct, but you need to be sure not to delete the one you are using and should save one older one that you know works just in case you have problems.

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

Some suggest this gui for many grub custom settings:
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by rostom_zer on 2011-06-29
ThanX guyZ, I did it :D

it was so easy

Best regards, rostom.

---

