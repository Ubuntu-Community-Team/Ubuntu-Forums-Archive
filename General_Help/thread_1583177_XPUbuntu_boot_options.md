---
title: "XP/Ubuntu boot options"
date: 2010-09-27
forum: General Help
---

### Post by Al_is_venting on 2010-09-27
So i installed an XP OS on a different partition of the HD, i know both systems are there but ubuntu somehow got the priority boot. i never get the option to boot in to XP.

Any input?

---

### Post by andrewthomas on 2010-09-27
Have you updated grub?

```
sudo update-grub
```

---

### Post by Rubi1200 on 2010-09-27
Could you please elaborate a little?

Did you install Windows _before_ or _after_ installing Ubuntu?

---

### Post by Al_is_venting on 2010-09-27
no, i don't know what that is. ill try it. 

What does that do though?

---

### Post by Quackers on 2010-09-27
sudo update-grub run from the terminal updates the grub bootloader. When it runs you should see that it recognises your Windows installation (unless something else is wrong)

---

### Post by Al_is_venting on 2010-09-28
i did it but still noting. WHen doing update it found 3 things one of which was the .bin for windows.

any more ideas?

---

### Post by Rubi1200 on 2010-09-28
Do you have an Ubuntu CD?

If yes, boot the computer and choose to try not install.

Then, from the LiveCD post the results of the bootscript linked at the bottom of my post.

Thanks.

---

