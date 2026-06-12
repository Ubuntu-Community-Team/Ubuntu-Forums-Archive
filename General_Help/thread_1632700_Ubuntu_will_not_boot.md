---
title: "Ubuntu will not boot"
date: 2010-11-28
forum: General Help
---

### Post by Kyley on 2010-11-28
So, I have been using lucid on my dell inspiron 1525 for a few months now, fine, untill it all imploded, now when I try to boot it I get the following; (enter appaling quality pic) [http://img24.imageshack.us/img24/1479/img2195656565656.jpg](http://img24.imageshack.us/img24/1479/img2195656565656.jpg)
 
with the live disc I can reinstall the OS, or "rescue a broken system" but fixing it, or at least being able to rescue the files from the hard drive would be gread, any advice would be much appreciated :D
 
EDIT: noobishly large pic :$

---

### Post by dino99 on 2010-11-28
seem that grub dont find the good path to boot (wrong uuid)

sudo grub-mkconfig
sudo update-grub

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Kyley on 2010-11-28
I tried that, I get ```
/bin/sh: sudo: not found
```
 
If the intention was to run that in terminal, I can't get onto the system without reinstalling the OS

---

### Post by karthick87 on 2010-11-28
@Kyley resize the image to smaller size.Or remove the image link and then attach it.It is very annoying.

---

### Post by dino99 on 2010-11-28
i believe too :(

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by drs305 on 2010-11-28
If you see the Grub menu first, press "e" to edit the menuentry and use the cursors and DEL key to remove the entire "search" line. Then CTRL-x to boot.

If that doesn't work:
Try removing and reinstalling Grub2 using a LiveCD (Ubuntu installation CD) and the chroot procedure found here. 
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")


If that isn't successful, please post the contents of RESULTS.txt, a file you generate by running the boot info script found here:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

