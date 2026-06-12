---
title: "Unable to mount volume, Need help about memory card"
date: 2009-07-08
forum: General Help
---

### Post by rushikesh988 on 2009-07-08
hello friends ,
I am havingtrouble with my MMC memory card of  my mobile ..

I think it is corrupted I was reciving picture from another mobile and suddenly it get corruped now I can't use it from mobile or from PC too ..is there is any way to repair it from UBUNTU ...

---

### Post by rushikesh988 on 2009-07-08
Anybody please

---

### Post by az on 2009-07-08
Image it and then try to pull files from the image


Install gddrescue and read the card to a file:

(Assuming that your memory card is devices sdb - change it to whatiever it is.)  To find out what the device it is, plug it in and then run "sudo lshw -C disk -short"

sudo ddrescue /dev/sdb1 image log

That creates an image of /dev/sdb1 and calls the file "image"  A log file is also created so that you can pause and resume the rescue.  You would want to do that if you have trouble reading the card and want to change card readers...

After the image is made, you can try to mount it:

mkdir mnt
sudo mount -o loop image mnt

If that is still corrupt, then you can try to pull files out without using the filesystem.

sudo apt-get install testdisk
(That will install testdisk and photorec.  Photorec is the software you want, it's a file-carver)

sudo photorec image
(That will run photorec on the image file.)

---

