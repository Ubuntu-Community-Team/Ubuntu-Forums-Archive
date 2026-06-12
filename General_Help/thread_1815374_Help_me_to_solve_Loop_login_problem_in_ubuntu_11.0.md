---
title: "Help me to solve Loop login problem in ubuntu 11.04"
date: 2011-07-31
forum: General Help
---

### Post by betruger on 2011-07-31
Hi 

I have an up-to-date ubuntu 11.04 system in multi-boot environment with Win XP and Win7 ultimate where grub2 is default boot loader.  
Yesterday, i have some strange problem that while entering username and password in login window, unity desktop could not load and the login screen come again like a 'loop'. i have tried to load ubuntu classic, safemode, no effect and some commands (as follows)
"sudo service gdm stop (then startx)
"sudo dpkg--reconfigure gdm"
"sudo apt-get --purge --reconfigure install gdm gnome-session"
 
But nothing were solve my problem. 

Pl help to solve the problem soon. 
My system config;  AMD Athlon 6400 3.2. GHz, 2GB DDR2, Nvidia 9600 GT Graphic card, Asus M3N*** motherboard. multiboot

---

### Post by betruger on 2011-08-01
bumped....!!!!!!!!!!!!!!!

---

### Post by dogeatery on 2011-08-02
I am having this VERY same problem with a netbook install of PeppermintOne OS -- except that I'm not dual booting anything.

I guess I'll just do a fresh installation but I'd prefer to learn how I can fix this problem in case it happens again.

---

### Post by cipherboy_loc on 2011-08-02
It looks like it is not a GDM issue but a Unity issue. Try re-installing unity (login to the Ubuntu Classic, start up Synaptic and look for the unity packages).


Cipherboy

---

### Post by dogeatery on 2011-08-02
> **cipherboy_loc said:**
> It looks like it is not a GDM issue but a Unity issue. Try re-installing unity (login to the Ubuntu Classic, start up Synaptic and look for the unity packages).


Cipherboy

What about my Peppermint install?  I don't have the option of loading Ubuntu Classic and I don't have Unity

---

### Post by Furball588 on 2011-08-02
Perhaps adding init 3 into your boot options so GDM does not start and then doing a 

metacity --replace


and the starting X would show some love

---

### Post by dogeatery on 2011-08-02
> **Furball588 said:**
> Perhaps adding init 3 into your boot options so GDM does not start and then doing a 

metacity --replace


and the starting X would show some love

I need clear instructions on how to do this.

---

