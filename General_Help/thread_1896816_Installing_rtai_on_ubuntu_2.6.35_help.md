---
title: "Installing rtai on ubuntu 2.6.35 help"
date: 2011-12-17
forum: General Help
---

### Post by chasing on 2011-12-17
i'm trying to install rtai package on ubuntu .using a new kernel ,the version is 2.6.32.2 ,i packed the rtai-3.8 to the ubuntu ,an /boot list is as follows &#65306;
-rw-r--r-- 1 root root 705737 2010-09-20 09:58 abi-2.6.35-22-generic
-rw-r--r-- 1 root root 110596 2011-12-17 13:38 config-2.6.32.2
-rw-r--r-- 1 root root 128592 2010-09-20 09:58 config-2.6.35-22-generic
drwxr-xr-x 3 root root 6144 2011-12-13 21:03 grub
-rw-r--r-- 1 root root 84203528 2011-12-17 13:40 initrd.img-2.6.32.2
-rw-r--r-- 1 root root 10767666 2011-12-13 21:19 initrd.img-2.6.35-22-generic
drwx------ 2 root root 12288 2011-12-13 20:42 lost+found
-rw-r--r-- 1 root root 165084 2010-09-25 01:14 memtest86+.bin
-rw-r--r-- 1 root root 167264 2010-09-25 01:14 memtest86+_multiboot.bin
-rw-r--r-- 1 root root 1798718 2011-12-17 13:38 System.map-2.6.32.2
-rw-r--r-- 1 root root 1830681 2010-09-20 09:58 System.map-2.6.35-22-generic
-rw-r--r-- 1 root root 1192 2010-09-20 10:01 vmcoreinfo-2.6.35-22-generic
-rw-r--r-- 1 root root 4106160 2011-12-17 13:38 vmlinuz-2.6.32.2
-rw-r--r-- 1 root root 4289584 2010-09-20 09:58 vmlinuz-2.6.35-22-generic
then ,I chang the grub.cfg as below:
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set c7d3eb3a-df6f-4aee-bed3-1f6c521ddae8
linux        /vmlinuz-2.6.35-22-generic root=UUID=a06d8b55-6ff1-47cf-b9b1-9f427dd42360 ro quiet splash
initrd        /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-2' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set c7d3eb3a-df6f-4aee-bed3-1f6c521ddae8
linux        /vmlinuz-2.6.32.2 root=UUID=a06d8b55-6ff1-47cf-b9b1-9f427dd42360 ro quiet splash
initrd        /initrd.img-2.6.32.2
}
but here is a problem :when i reboot the computer and choose the new kernel ,the computer doesn't work,it turns out a black screen with a cursor blinking on the left top . So what should i do next ,please help?Thanks

---

