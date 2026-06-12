---
title: "GDM not loading correctly"
date: 2010-08-28
forum: General Help
---

### Post by maxd123 on 2010-08-28
hi, i have been using ubuntu for a while and today when i booted up all there is are the cursor and background in the login area.

I was able to log in by doing CTRL+ALT+F2 then sudo /etc/init.d/gdm stop then startx but all the gnome applets are missing and i get a warning to delete them or not to. :(

what information do i have to give to you for help?

sorry if its a easy problem i'm new to ubuntu

---

### Post by maxd123 on 2010-08-28
i am using 10.04 btw

---

### Post by goldenbrown on 2010-08-28
TYPE
sudo apt-get start gdm
> **maxd123 said:**
> hi, i have been using ubuntu for a while and today when i booted up all there is are the cursor and background in the login area.

I was able to log in by doing CTRL+ALT+F2 then sudo /etc/init.d/gdm stop then startx but all the gnome applets are missing and i get a warning to delete them or not to. :(

what information do i have to give to you for help?

sorry if its a easy problem i'm new to ubuntu

---

### Post by Silent Warrior on 2010-08-28
That doesn't sound like something I know how to help with... What graphics hardware and driver are you using? What kernel? Made any recent updates, or attempted to change GDM appearance? Is the computer home-built, or some OEM-wossname?
Tried running 'sudo dpkg-reconfigure gdm'? As an extreme measure, you can also try installing another display-manager; kdm, lxdm.

Edit: goldenbrown: Are you sure that 'start' is a valid apt-get action? :)

---

### Post by maxd123 on 2010-08-28
Thanks for your answers, i fixed it, the problem was that i installed zlib from source earlier for pcsx2 and somehow it was screwing up everything so i uninstalled it and now everythings back to normal :popcorn:

---

