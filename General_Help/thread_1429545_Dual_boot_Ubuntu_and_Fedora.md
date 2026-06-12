---
title: "Dual boot Ubuntu and Fedora"
date: 2010-03-14
forum: General Help
---

### Post by Roie on 2010-03-14
Hello
last week i've installed ubuntu 9.04 on my comupter when already had fedora12.
since the installation i can't get into fedora, it seems the grub of ubuntu don't recogized it.
i've looked for a lot of help in google, but nothing worked.
how can i change my  /boot/grub/menu.1st so it would recognize my fedora ?

here are some details 
my /boot of fedora is on /dev/sda2
when i mount it and do ls, this is the output
-rw-r--r-- 1 root root   160280 2009-10-13 21:13 memtest86+-4.00
-rw-r--r-- 1 root root   161956 2009-10-13 21:13 elf-memtest86+-4.00
drwxr-xr-x 3 root root     1024 2009-11-09 21:35 efi
-rwxr-xr-x 1 root root  3429536 2010-02-11 09:20 vmlinuz-2.6.31.12-174.2.19.fc12.x86_64
-rw-r--r-- 1 root root  1872724 2010-02-11 09:20 System.map-2.6.31.12-174.2.19.fc12.x86_64
-rw-r--r-- 1 root root    97992 2010-02-11 09:20 config-2.6.31.12-174.2.19.fc12.x86_64
drwx------ 2 root root    12288 2010-02-18 23:57 lost+found
-rw-r--r-- 1 root root 11358736 2010-02-19 19:07 initramfs-2.6.31.12-174.2.19.fc12.x86_64.img
-rwxr-xr-x 1 root root  3429472 2010-02-19 21:08 vmlinuz-2.6.31.12-174.2.22.fc12.x86_64
-rw-r--r-- 1 root root  1872763 2010-02-19 21:08 System.map-2.6.31.12-174.2.22.fc12.x86_64
-rw-r--r-- 1 root root    97992 2010-02-19 21:08 config-2.6.31.12-174.2.22.fc12.x86_64
-rw-r--r-- 1 root root 12236824 2010-02-20 18:01 initramfs-2.6.31.12-174.2.22.fc12.x86_64-nouveau.img
-rwxr-xr-x 1 root root  3603328 2010-02-27 11:40 vmlinuz-2.6.32.9-67.fc12.x86_64
-rw-r--r-- 1 root root  2098865 2010-02-27 11:40 System.map-2.6.32.9-67.fc12.x86_64
-rw-r--r-- 1 root root   101134 2010-02-27 11:40 config-2.6.32.9-67.fc12.x86_64
-rw-r--r-- 1 root root 12240258 2010-02-27 14:49 initramfs-2.6.31.12-174.2.22.fc12.x86_64.img
-rw-r--r-- 1 root root 12554626 2010-03-06 15:18 initramfs-2.6.32.9-67.fc12.x86_64.img
drwxr-xr-x 2 root root     1024 2010-03-06 15:18 grub

the output of blkid is 
/dev/sda2: UUID="44655ec8-d182-48b8-a52b-d435d4b77a4c" TYPE="ext4" 

thanks for the help

---

### Post by byStanderone on 2010-03-14
...take a look at your fstab file ( /etc/fstab )...and compare the uuid that you got thru blkid...edit fstab if necessary.

---

### Post by Roie on 2010-03-14
i don't have it at the fstab
to do ls i needed to mount it..

---

### Post by oldfred on 2010-03-14
With grub legacy and multiple operating systems I liked to chainboot as then each operating systems updates were automatically updated in their local menu.lst.

I have seen both grub2 update correctly and issues with grub2 updating for Fedora as it looked for initrd and Fedora uses initramfs. 

You may be able to convert a grub2 entry back to grub legacy or copy your Fedora entry into Ubuntu's menu.lst?

To see your entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

