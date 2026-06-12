---
title: "win7 (in dualboot) won't boot after resizing prtns w/Gparted"
date: 2012-01-19
forum: General Help
---

### Post by doron387 on 2012-01-19
well, after a lot of searching i have decided to ask here.
i had win7/ubutu 10.10 32bit dualbooting on Asus 1201N for long time peacfully until i decided to give 10.10 64bit a try also.
i had 92 gb sda1 ntfs partition for win7
and a 190 gb sda4 extended partition with: 
10 gb ubuntu root, 
10 gb ubuntu home, 
4 gb ubuntu swap 
and the rest was big ntfs data partition.
i have tried to resize the win7 partition with it's own partition editor after defragmentation but it did not let me do it. 
so i went to gparted, using an ubuntu live usb, and resized it.
operation was succesfull, except for the fact that now, when i turn the machine on, i get the first menu ubuntu/or/win7, 
and whatever option that i choose it gets to a windows black screen that says :
windows boot manager
windows failed to start. a recent hardware or software change might be the cause. try to fix the problem :
1. insert your windows installation disc and restart your computer.
2. choose your language settings, and then click "next".
3. click "repair your computer"
if you do not have this disk, contact your system administartor or computer manufacturer for assistance.

file : \NST\AutoNeoGrub0.mbr
status : 0x0000225

info : the selected entry could not be loaded because the application is missing or corrupt.

any ideas ?

EDIT : well, i have found a copy of the windows 7 recovery iso in my files (luckily i saved it), i installed it on a usb thun=mb drive using usbmultiboot and i booted from the usb, it went into windows 7 recovery options - and voila. it works.
solved.

---

### Post by Rubi1200 on 2012-01-20
Please mark your thread Solved using the Thread Tools near the top of the page.

Thanks.

---

