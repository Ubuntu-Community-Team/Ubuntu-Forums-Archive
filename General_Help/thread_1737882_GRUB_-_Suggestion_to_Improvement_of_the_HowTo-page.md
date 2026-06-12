---
title: "GRUB - Suggestion to Improvement of the HowTo-pages"
date: 2011-04-24
forum: General Help
---

### Post by Aetixintro on 2011-04-24
Under the Creating the Custom Menu of the [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2), I think one should ADD the following:

Please...
Copy the content of your grub.cfg in /boot/grub where this file is.

Copy this content into your 40_custom in /etc/grub.d where this file is.

*Only *preserve the menu-entries from this file, grub.cfg. You delete the rest. Also make sure you preserve the HEADER of 40_custom. You can also rename 40_custom to 06_my_linux or something.

Then **empty** the  /etc/grub.d and let the 4 files remain: 00_header, 05_debian_theme, 06_my_linux and README. The files you remove from the directory, you can put in your Home folder. You may also make a back-up copy of the 40_custom.

End.

When this has been done, I still get the problem of *double listing*. My entries in the 40_custom file is getting listed twice. Can anyone help me with this, please? Is there a generic rule that needs to commented out? From let's say 05_debian_theme?

This for now. Cheers! :)

---

### Post by ksprasad on 2011-04-25
Hi,
 
 Make sure you have executed 'sudo update-grub' at the end.
 
 By the way, you dont have to remove the files from grub.d directory. You just need to remove the  execution permission of those files. 
 
Regards,
ksprasad

---

### Post by uRock on 2011-04-25
Duplicate thread in Tutorials and Tips awaiting approval.

[http://ubuntuforums.org/showthread.php?t=1737872](http://ubuntuforums.org/showthread.php?t=1737872)

---

### Post by Elfy on 2011-04-25
moved back to general help - duplicate in tutes'n'tips is deleted.

---

