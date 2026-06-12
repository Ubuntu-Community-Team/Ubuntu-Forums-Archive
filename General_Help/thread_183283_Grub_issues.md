---
title: "Grub issues"
date: 2006-05-27
forum: General Help
---

### Post by Trab on 2006-05-27
hello, i hate grub.

with that outta the way, ive solved MOST of my grub issues, but i still have one.

windows wont boot.
this is a common issue that ive solved before, but its always difficult to do

how my computer is set up is:
1 IDE HD with Windows, known as HDA 
(i have /dev/hda1 mounted on linux, and it IS windows)
1 SATA drive broken down into a few partions
SDA1 is just 20gb and i use it as misc storage space
sda2 is ubuntu's root
sda3 is my /home
sda4 is swap space

the problem is, when i boot into grub my linux setup which works fine is:

title		Ubuntu, kernel 2.6.15-23-k7
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-k7 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-k7
savedefault
boot

whereas windows, which is currently setup as thus:
title		WinXP Pr0
root		(hd1,0)
savedefault
makeactive
chainloader +1 

and it doesnt work.

im tired of trying to figure out how to make this work, ive read 4 manuals and copous amounts of tutorials on how to fix this, but it doesnt work.
could someone just give me the answer that works?
thanks
-Trab

---

### Post by Mustard on 2006-05-27
> root (hd1,0)
If windows is on /dev/hda1, then why would you be using (hd1,0) in grub?  Shouldn't it be (hd0,0) ?

(hd1,0) = second drive, first partition
(hd0,0) = first drive, first partition

---

### Post by Trab on 2006-05-27
yes, but root (hd0,1) works to boot linux, which is the Sata drive, second partion.
therefore, the sata drive is (hd0) and so the IDE drive is probably (hd1)

---

### Post by Mustard on 2006-05-27
[QUOTE=Trab]yes, but root (hd0,1) works to boot linux, which is the Sata drive, second partion.
therefore, the sata drive is (hd0) and so the IDE drive is probably (hd1)[/QUOTE]
Have you tried changing the windows section to (hd0,0)?

Whats the output of this command..

```
sudo fdisk -l
```

---

### Post by Trab on 2006-05-27
(hd0,0) wouldnt work, because 1st HD 1st partion is a 20gb place for storage.

```

tedd@raptor:~$ sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2442    19615333+  83  Linux
/dev/sda2   *        2443       15496   104856255   83  Linux
/dev/sda3           15497       30385   119595892+  83  Linux
/dev/sda4           30386       30515     1044225   82  Linux swap / Solaris

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2433    19543041    7  HPFS/NTFS

Disk /dev/sdd: 131 MB, 131072000 bytes
16 heads, 32 sectors/track, 500 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         500      127976+   6  FAT16
tedd@raptor:~$

```

---

### Post by Mustard on 2006-05-27
If windows isn't on the first hard drive then you would have to use the map commands in grub to tricking into thinking it was on the first drive I would think.

My win98 is on my slave drive, and I access it using this grub entry...

```
title           Windows 95/98/Me
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

Try adding these two lines and see how you go..

```
map             (hd0) (hd1)
map             (hd1) (hd0)
```

---

