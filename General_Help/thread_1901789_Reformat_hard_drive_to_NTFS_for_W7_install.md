---
title: "Reformat hard drive to NTFS for W7 install"
date: 2011-12-29
forum: General Help
---

### Post by sevendaughters on 2011-12-29
Hello everyone. I'll try and explain this with as much clarity as I can, though I am moderately technophobic.

I am attempting to install W7 onto a laptop which is currently running the latest edition of Ubuntu. I would like to completely eradicate all traces of Ubuntu like a wishful murderer. 

During the install for W7, it tells me that I cannot proceed as the hard drive is not formatted to a compatible degree and that it needs to be NTFS. This stage looks like this (not mine, just an example).

[IMG]http://apcmag.com/images/apcapc/howto/dualboot_vista_windows7_vista_first/vista_windows7_install_01.jpg[/IMG]

After some cursory googling and poking around here and Microsoft support, I see many people recommending GParted as the tool required to cure the ailment. 

However, GParted will not let me perform the task. I presume it is because I am trying to reformat the drive that is currently in use. This is the GParted screen shot (apologies for the white edges, bad edit)

[IMG]http://i223.photobucket.com/albums/dd176/danielthomasbrookes/gparted.jpg[/IMG]

From here on in I am stumped. Can anybody help?

---

### Post by Elfy on 2011-12-29
Boot with a livecd/usb - open gparted.Right click on swap if it's mounted - swapoff.

No partitions should be mounted now - delete - apply.

Remove livecd.

Do whatever you need to with the win disk.

---

### Post by sevendaughters on 2011-12-29
This works, thanks.

Also it is possible to delete unwanted partitions from the W7 install, I was just being an idiot there.

---

### Post by Elfy on 2011-12-29
Absolutely no idea at all - last windows I used was w2k.

---

### Post by alphaamanitin on 2011-12-29
You should mark this thread as solved.  And to any others that come here, look at the first screenshot of the windows 7 install, if you click on drive options it will let you delete, reformat, etc the drives without having to use GParted.  

AlphaA

---

