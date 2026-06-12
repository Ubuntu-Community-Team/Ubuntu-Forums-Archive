---
title: "Grub menu is basically empty and i cant rebuild it!"
date: 2010-04-23
forum: General Help
---

### Post by linuxd00 on 2010-04-23
So basically this happened:
i have 9.10  on my dual boot machine (ubuntu WinXP) and did a package update 2 days ago for the first time in 3 months. Kernel .21 was installed after having .17

Dont know if this part had anything to do but ill tell you anyway: during the update the computer (ibm Thinkpad x31) froze. After restart i did "dpkg --reconfigure -a" or something similar that apt-get told me to do.

now after rebooting the Grub2menu does not list any OSes... only a Memtest entry.

i rebooted using 

```
grub> linux   (hd0,7)/boot/vmlinuz-2.6.27-9-generic root=/dev/sda7
grub> initrd  (hd0,7)/boot/initrd.img-2.6.27-9-generic
grub> boot
```

and did 

```
sudo os-prober

sudo update-grub
sudo update-grub2

```

os-prober found the WinXP installation... but update-grub (and update-grub2) only list "Memtest" :( so the grub menu is basically empty.

 i still am able to boot into linux from the grub command line using the commands above... but i'd love to have my menu back and to use windows again as i need it for work!

this is the content of the /boot dir.. if it helps.. i noticed only memtest has a bin file:

```
total 56192
drwxr-xr-x  3 root root    4096 2010-04-22 12:10 .
drwxr-xr-x 21 root root    4096 2010-04-22 12:07 ..
-rw-r--r--  1 root root  629174 2009-10-16 14:03 abi-2.6.31-14-generic
-rw-r--r--  1 root root  629174 2009-12-08 04:03 abi-2.6.31-16-generic
-rw-r--r--  1 root root  629446 2009-12-10 15:33 abi-2.6.31-17-generic
-rw-r--r--  1 root root  629853 2010-03-24 07:31 abi-2.6.31-21-generic
-rw-r--r--  1 root root  111371 2009-10-16 14:03 config-2.6.31-14-generic
-rw-r--r--  1 root root  111371 2009-12-08 04:03 config-2.6.31-16-generic
-rw-r--r--  1 root root  111371 2009-12-10 15:33 config-2.6.31-17-generic
-rw-r--r--  1 root root  111349 2010-03-24 07:31 config-2.6.31-21-generic
drwxr-xr-x  2 root root    4096 2010-04-23 21:07 grub
-rw-r--r--  1 root root 7650984 2009-12-14 00:13 initrd.img-2.6.31-14-generic
-rw-r--r--  1 root root 7651670 2009-12-14 00:33 initrd.img-2.6.31-16-generic
-rw-r--r--  1 root root 8415111 2010-04-09 20:42 initrd.img-2.6.31-17-generic
-rw-r--r--  1 root root 8420781 2010-04-22 12:10 initrd.img-2.6.31-21-generic
-rw-r--r--  1 root root  128796 2009-10-23 12:11 memtest86+.bin
-rw-r--r--  1 root root 1664737 2009-10-16 14:03 System.map-2.6.31-14-generic
-rw-r--r--  1 root root 1665323 2009-12-08 04:03 System.map-2.6.31-16-generic
-rw-r--r--  1 root root 1665500 2009-12-10 15:33 System.map-2.6.31-17-generic
-rw-r--r--  1 root root 1668296 2010-03-24 07:31 System.map-2.6.31-21-generic
-rw-r--r--  1 root root    1196 2009-10-16 14:06 vmcoreinfo-2.6.31-14-generic
-rw-r--r--  1 root root    1196 2009-12-08 04:05 vmcoreinfo-2.6.31-16-generic
-rw-r--r--  1 root root    1196 2009-12-10 15:35 vmcoreinfo-2.6.31-17-generic
-rw-r--r--  1 root root    1196 2010-03-24 07:33 vmcoreinfo-2.6.31-21-generic
-rw-r--r--  1 root root 3890400 2009-10-16 14:03 vmlinuz-2.6.31-14-generic
-rw-r--r--  1 root root 3892032 2009-12-08 04:03 vmlinuz-2.6.31-16-generic
-rw-r--r--  1 root root 3890560 2009-12-10 15:33 vmlinuz-2.6.31-17-generic
-rw-r--r--  1 root root 3901472 2010-03-24 07:31 vmlinuz-2.6.31-21-generic
```

---

### Post by drs305 on 2010-04-23
If you only have memtest86+ I suspect your /etc/grub.d folder is either empty or the files are not executable.

Take a look at the folder. If there are about half a dozen files, such as 00_header, 10_linux, etc, make sure they are executable with the following command:
```
sudo chmod +x /etc/grub.d/*_*
```

If the files are missing, reinstall grub-pc:
```
sudo apt-get install --reinstall grub-pc
sudo update-grub
```

**Added: If the files still don't exist in /etc/grub.d:**
Make sure you have an internet connection and reliable power source, as you will temporarily have no bootloader (answer Yes).
```
sudo apt-get purge grub-common grub-pc
sudo apt-get install grub-common grub-pc
```
This will recreate the files.

---

### Post by ScarySquirrel on 2010-04-23
Hehe. Have fun with that. On a related note: 

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1460549]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1460549")

Also, have you tried holding the shift key during boot? 
That helps.

---

### Post by linuxd00 on 2010-04-24
Thanks drs305!! only reinstalling didnt work.. but purging and installing did it!! its working as great as ever!

---

