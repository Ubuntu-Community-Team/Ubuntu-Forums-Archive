---
title: "How can i get Grub2 find newly installed o/s"
date: 2010-03-19
forum: General Help
---

### Post by HandLotion on 2010-03-19
I'm playing with my hard drive partitions and trying out different O/S versions so I want Grub2 to be aware of them on its boot menu.  Currently I'm using the maintainer's version of Grub2 that came with karmic.  Do I have to do a re-install of Grub2 or is there a makefile I can use?  Specific commands that I would need be nice.

Any insights would be helpful.

---

### Post by perham on 2010-03-19
> **HandLotion said:**
> I'm playing with my hard drive partitions and trying out different O/S versions so I want Grub2 to be aware of them on its boot menu.  Currently I'm using the maintainer's version of Grub2 that came with karmic.  Do I have to do a re-install of Grub2 or is there a makefile I can use?  Specific commands that I would need be nice.

Any insights would be helpful.

this should do the trick:

```
sudo update-grub 
```

---

### Post by Chesamo on 2010-03-19
```
sudo update-grub
```

EDIT: Ah, I got ninja'd!

---

### Post by HandLotion on 2010-03-22
> **Chesamo said:**
> ```
sudo update-grub
```EDIT: Ah, I got ninja'd!

You meant grub2, didn't ya. And how do I make sure I'm getting the maintainer's version? Or is that not important.

---

### Post by drs305 on 2010-03-22
If you are running Grub2, you don't need to use "update-grub2" - "update-grub" will know it's Grub 2. Or if you really want to be sure, you can run the command as "sudo grub-mkconfig -o /boot/grub/grub.cfg".

Running that command isn't updating the grub *installation*, it is just running the current Grub2 scripts, so you won't be asked if you want to get the maintainer's version. The scripts will search your partitions for existing linux, windows, OSX and maybe hurd (depending on the version of grub you are running). Hopefully your other OSs will be seen and automatically added to the menu.

When actually updating the Grub installation, you would be asked if you want to keep your current files or update to the maintainer's version. Improvements to this function include now giving you the ability to view your current and proposed files, differences between them, and also will give you the ability to merge the two if you wish. Normally I accept the maintainer's version since it would include improvements that you might not get if you keep your current files.

---

### Post by HandLotion on 2010-03-23
Thanks. This is exactly what I needed to know.

---

