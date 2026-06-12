---
title: "Selecting Grub2 splash images?"
date: 2010-03-28
forum: General Help
---

### Post by oxf on 2010-03-28
HI,

I just installed the Grub2 splash images package in Synaptic. The documentation explains how to install them, but I dont see any reference to previewing them. Is there a way I can preview them and see what's available before I decide to install? 

Thanks!

---

### Post by drs305 on 2010-03-28
You can open gimp and then "File, Open" and put "/usr/share/images/grub" in the location bar and press ENTER. That will list the files in that folder, with a preview in the right pane. You could then open any that you would like to get a closer look at.

---

### Post by oxf on 2010-03-28
> **drs305 said:**
> You can open gimp and then "File, Open" and put "/usr/share/images/grub" in the location bar and press ENTER. That will list the files in that folder, with a preview in the right pane. You could then open any that you would like to get a closer look at.

OK thanks! Now I know where they are located they are the file browser displays the thumb nails.

---

### Post by drs305 on 2010-03-28
When you decide to install one, remember they are not in the default folder listed in /etc/grub.d/05_debian_theme.  You will either need to copy the image into the default folder (/usr/share/images/desktop-base) or change the location. 

There are differing versions of Grub2 [noparse](1.97 beta and 1.98)[/noparse] available to Ubuntu users, depending on which release you are using. The older version uses the line "for i in ..." while the newer release uses "WALLPAPER=" to set the background image. 

If you need help with this, refer to the Ubuntu community doc:
[https://help.ubuntu.com/community/Grub2#GRUB%202%20Splash%20Images]("https://help.ubuntu.com/community/Grub2#GRUB%202%20Splash%20Images")

---

