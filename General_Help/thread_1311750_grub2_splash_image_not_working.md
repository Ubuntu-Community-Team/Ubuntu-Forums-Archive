---
title: "grub2 splash image not working"
date: 2009-11-02
forum: General Help
---

### Post by 565Customz on 2009-11-02
saved a image file as the correct size and format (tga) and edited the config file   "/etc/grub.d/05_debian_theme"

 i change the part of the file name that said "desktop.base" to "grub" (which is where i saved the picture)

when i do sudo updat-grub, it shows that it finds the kernel headers but doesn't find the .tga image. 

can anyone help?

also i followed the guide "grub2 basics" in the tuturials section.

thanks

---

### Post by Jaymac on 2009-11-04
I'm having the exact same issue.  I've edited the required line, saved my file in the correct folder as a tga and have run update-grub (and update-grub2 - what is the difference?).  Anyone have a solution?

---

### Post by Jaymac on 2009-11-04
D'oh - just fixed it.  My 05_debian_theme file was not executable :)

---

### Post by 565Customz on 2009-11-06
what did you do to make it executable?

---

