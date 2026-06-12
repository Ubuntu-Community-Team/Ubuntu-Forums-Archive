---
title: "USB Drive Problems"
date: 2010-12-30
forum: General Help
---

### Post by garricks on 2010-12-30
My wife has put some pictures on her usb drive & trying to print them off at a few instant photo machines but they all say no pictures can be found?

I'm running Ubuntu 10.10 on my laptop, is there any way to make her usb drive recognisable to these machines and any other Windows system?

---

### Post by Nytram on 2010-12-30
Backup the data on your usb drive and then format it as a fat32 filesystem (can be done in either windows or ubuntu.) After you move your photos back onto the drive, they should be recognisable in windows, ubuntu and the photo machines.

---

### Post by garricks on 2010-12-30
Reformatted it with G parted last night after the first failed attempt.

Shows up as 'msdos' in file type when I click properties after reformatting it as fat32 which it done before and the machines still didn't read it today but I will try it tomorrow and hopefully it will work.

---

### Post by Dex73 on 2010-12-30
Also may want to check the file type. My sister in law has a camera that takes photos in a rediculus format. I had to download plugins on my laptop running Ubuntu 10.04. Does it not reconnize the usb format or the pitcher?

---

### Post by garricks on 2010-12-30
All pictures are Jpegs. 

The machines we have tried have said there are no pictures on the device but when I plug it back into my laptop (running Ubuntu) the pictures are still there?

---

### Post by oldfred on 2010-12-30
msdos is the partitioning scheme, also known as MBR, with the 4 partition limit. One other one is gpt used by Macs.

I has issues where my files were .JPG but anther program would not see them. I changed them to .jpg and then it saw them. To me any useful program would work with either .JPG or .jpg or .Jpg. Case should not matter in this case.:)

---

### Post by srs5694 on 2010-12-31
Also, post the output of "sudo fdisk -lu /dev/sd{x}", where "{x}" is the letter associated with the USB device. Please post the output between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. This will help us see what your partitioning scheme is. It's possible there's something strange about it, like multiple partitions (Windows expects just one partition on a USB flash drive) or an incorrect partition type code.

---

