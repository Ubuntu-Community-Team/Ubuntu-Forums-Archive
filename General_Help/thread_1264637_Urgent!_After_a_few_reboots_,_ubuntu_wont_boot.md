---
title: "Urgent! After a few reboots , ubuntu wont boot?"
date: 2009-09-12
forum: General Help
---

### Post by mac666 on 2009-09-12
Hey! 
Today ive been rebooting my computer 20 times, ive been trying to configure /etc/fstab to do as i command, but it didnt really work out for me;
Now i cant get X-Server to boot along with my computer. It gives me a big BLUE terminal on my screen (After Ubuntu boot logo) saying something like X-Server couldnt start bla bla bla - fix it and then restart GDM (Or something)

Then i get put login screen in terminal... 
I opened Fstab, changed back to last settings but i cant save, its a read only filesystem...
Could this have with it to do?
I Havnt touched the nvidia drivers for a while but i do have the beta drivers... could it be that? I cant uninstall them since its in "read only mode"?

Thanks...:confused:

---

### Post by konnorrigby on 2009-09-12
try to login as root and change your setting

---

### Post by mac666 on 2009-09-12
> **konnorrigby said:**
> try to login as root and change your setting
i dont have root password, the ubuntu installation bugs and i can never set the root password
how ever i cant save any settings since its in read only mode

---

### Post by mac666 on 2009-09-12
Come on guys, someone must know whats up, or how to make it a read write system, so at least i can uninstall the drivers?
Please

---

### Post by dumblebee100 on 2009-09-12
use a live CD 

when I get similar error I used to boot through live CD and mount ubuntu partition and then edit those fstab and xorg files 

since u know what all changes you did and you can revert back to defaults 


but anyways please post the files of your xorg.conf and fstab files ..so that we can check if there is really some error 

generally xserver dont start when there is problem in xorg.conf ..atleast in my experience ....but there are lot many factors

---

