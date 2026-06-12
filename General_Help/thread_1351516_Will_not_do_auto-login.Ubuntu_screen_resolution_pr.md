---
title: "Will not do auto-login.Ubuntu screen resolution problems:    I had changed my desktop"
date: 2009-12-10
forum: General Help
---

### Post by t616 on 2009-12-10
[FONT=Comic Sans MS]Ubuntu screen resolution problems:
 
 I had changed my desktop screen resolution from 1153 x 864 to 1024 x 768 so my great-grandson would have larger icons to work with. After doing a restart, 9.10 would not Auto-login and went to a never ending Login loop.  

I had to power off and on several times before the Grub selection screen would appear. (I've since learned, that if you hit the space-bar when booting the grub selection screen will appear). I chose recovery mode and at the command prompt I entered user name and password. I then entered "sudo gdm" which returned me to my normal desk top.

I changed the desktop resolution back to 1153 x 864. Did a restart and auto-login worked perfectly.

Auto-login will not work if the screen resolution select by Ubuntu at installation time is different from the desktop screen resolution. Seems like a big problem when changing your desktop resolution can cause you system to become unavailable. Seem like both should always be set from the same screen or fix it so the difference doesn't matter. 

Also the "Login Screen Settings" window allowed me to unlock it one time. Ever since Clicking on the unlock button has no effect, not even an error message.

[/FONT]Any help is appreciated. Thanks!

---

### Post by simple simon on 2009-12-22
bump.  I also have similar problems.

How does one set the login screen resolution!

---

### Post by simple simon on 2010-01-18
Have had to disable gdm.  Boots fine to command line and startx works without hitch.

Does anyone know how to set the login screen resolution?

---

### Post by j_neish on 2010-02-02
Try looking at my similar/same problem here
[http://ubuntuforums.org/showpost.php?p=8726825&postcount=44](http://ubuntuforums.org/showpost.php?p=8726825&postcount=44)
maybe you can also patch over the cracks in Ubuntu.

---

