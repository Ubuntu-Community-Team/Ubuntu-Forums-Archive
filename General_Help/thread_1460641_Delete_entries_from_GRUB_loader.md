---
title: "Delete entries from GRUB loader?"
date: 2010-04-23
forum: General Help
---

### Post by KarmicKlot on 2010-04-23
My laptop is set to dual boot, either Ubuntu 9.10 or Windows Vista. The GRUB loader has multiple entries, starting with Ubuntu, then several instances of Ubuntu recovery mode, before memory test and two entries for Vista, the first of which does not work.
 
How do I delete the unwanted entries? I can press "e" to edit them, but if I do so how do I actually delete them, assuming it is safe to do so.

---

### Post by bigsmitty64 on 2010-04-23
Go [HERE]("http://ubuntuforums.org/showthread.php?t=1195275") and read entry #7 
Good luck,
Smitty

---

### Post by ambdeep on 2010-04-23
just got to the terminal....enter the below code and remove the entries you dont want.....simple...
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by bigsmitty64 on 2010-04-23
If I'm not mistaken 9.10 introduced  grub2  right? which means there is  no ''/boot/grub/menu.lst''. It has been replaced by  ''/boot/grub/grub.cfg",  which is not supposed to be edited at all.

To the Original poster:
I would check to see which grub you have, if it is (I think) 1.97,  then that is considered grub2.  And you should follow the link I provided. If it is grub legacy (grub1) then what ambdeep said will work.

---

### Post by StuartN on 2010-04-23
Just open the Synaptic Package Manager and uninstall the old kernels that you no longer want. Search for installed packages called linux-image-2.6.xx-xx-generic and make sure not to uninstall the latest kernel. Grub will be updated automatically.

---

### Post by KarmicKlot on 2010-04-23
Thank you for that.  I have now reduced the list to manageable proportions.

---

### Post by KarmicKlot on 2010-04-23
Just a PS to let you know why I had to reduce the list.  The Vista loader was right at the bottom, and was not visible anymore.  I did not notice the little down arrow in GRUB and thought that Vista had failed, so I reinstalled it from the hidden partition, and still could not find how to run it.  When I did notice the down arrow and loaded Windows I had to start over reloading all my programs and documents and getting rid of most of the programs that came with the manufacturers setup.  At least I now have a clean Windows install for the one thing that I do need to run in Windows, which is a yacht navigation program with a USB GPS device that only seems to work in Windows.  Everything else I use works just fine in Ubuntu, and faster than it did in Vista, except for one web based internet banking access terminal which is Windows Internet Explorer 6 or above based.

---

### Post by StuartN on 2010-04-23
> **KarmicKlot said:**
> The Vista loader was right at the bottom

You can make another operating system the default or even the first entry in Grub 2 following the instructions here [http://ubuntuforums.org/showthread.php?t=1400750](http://ubuntuforums.org/showthread.php?t=1400750)

---

