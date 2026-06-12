---
title: "noob on ubuntu  i have 2 problems if any one can help"
date: 2012-05-08
forum: General Help
---

### Post by qball1234 on 2012-05-08
Hi all 

 1st i have windows and ubuntu iv just updated ubuntu to the new one and now theres no option to load windows up when i turn it on has any one any ideas

2nd im just wrighting up my cv to send to a job what kind of file do i want to save it as so it can be opened on  windows comp   (docx)  (doc) (pdb) i havent got a clue theres loads of them

thanks all

---

### Post by Cheesemill on 2012-05-08
I would go for .doc

It's probably the most compatible.

---

### Post by Baldrick_NZ on 2012-05-08
Hi, and welcome to the forums!

1/ in terminal go```
sudo update-grub
```you'll be prompted to enter your password. This should generate something like this```
Generating grub.cfg ...
using custom appearance settings
Found background image: /home/baldrick/Pictures/Maraetaibeforesunrise.jpg
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done

``` The key is what you see at the end of the output. In my case, "Found Windows Vista (loader) on /dev/sda1".
This means grub has now found my Windows partition. If this is the same for you, re-boot and you'll get the choice of O/S to boot into.

2/ I'd export your CV as a PDF file and send that. I'd also save a local copy for your own personal use in whatever format you like.

Hope this helps.

---

### Post by qball1234 on 2012-05-08
i thort pdf at the stat but theres no option for it. went for the doc

i tryed the terminal all i got was. ill reboot it see if its done any thing 

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin

thanksfor the help

---

### Post by Baldrick_NZ on 2012-05-08
> **qball1234 said:**
> i thort pdf at the stat but theres no option for it. went for the doc

i tryed the terminal all i got was. ill reboot it see if its done any thing 

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin

thanksfor the help

So you have 2 Linux kernels, one really old and the other is the latest, and no windows. Hmmm... So there was nothing after "Found memtest86+ image: /boot/memtest86+.bin"?

Are you using Libreoffice for #2?

---

### Post by westie457 on 2012-05-08
Hi what is the output of ```
sudo fdisk -l
``` please.

the l is a small L

---

### Post by Paqman on 2012-05-08
> **Baldrick_NZ said:**
> I'd export your CV as a PDF file and send that.

This. PDF is the only format that you can be sure it'll look the same on the reader's machine as on yours. Going for .doc is a bit fraught. They'll be able to open it, but can you be sure the formatting will be ok in whatever version of Office they have? Not worth the risk IMO.

You can export to PDF through the print dialog.

---

### Post by qball1234 on 2012-05-09
no nothing after  Found memtest86+ image: /boot/memtest86+.bin   that was it

---

### Post by qball1234 on 2012-05-09
> **westie457 said:**
> Hi what is the output of ```
sudo fdisk -l
``` please.

the l is a small L


hi thanks for helping iv done that code  ]sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x27cb27ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   103828639    51914288+   7  HPFS/NTFS/exFAT
/dev/sda2       103829502   156301311    26235905    5  Extended
/dev/sda5       103829504   154992639    25581568   83  Linux
/dev/sda6       154994688   156301311      653312   82  Linux swap / Solaris

would it be easyer just to reset it back to the old ubuntu then use disk to update it.

---

### Post by qball1234 on 2012-05-09
> **Paqman said:**
> This. PDF is the only format that you can be sure it'll look the same on the reader's machine as on yours. Going for .doc is a bit fraught. They'll be able to open it, but can you be sure the formatting will be ok in whatever version of Office they have? Not worth the risk IMO.

You can export to PDF through the print dialog.


thanks pal good to know

---

