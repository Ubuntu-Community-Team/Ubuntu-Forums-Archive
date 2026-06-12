---
title: "Burg"
date: 2011-08-13
forum: General Help
---

### Post by nankura on 2011-08-13
hey guys

i found this guide but i have a phew questions

[http://www.omgubuntu.co.uk/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/](http://www.omgubuntu.co.uk/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/)

Does this process also apply to Kubuntu 11.04?

I want to be safe. so is there any necessary preperations to installing BURG. like, removing the current grub, kernel changes, reinstalling nvidia drivers

Also the install part says hd0, im not sure were my installation is hd0 wise.

Kubuntu is installed on the drive /dev/sdc and its the main drive in the bios. boot drive

i just wanna be safe and make sure i do everything right, but i really like burg. i used it on another distro. and the theme stuff rocks

---

### Post by raja.genupula on 2011-08-13
burg worked for me in 11.04 . you can go with it . no grub folder will be in your boot dir but its override by burg . if you uninstall i think grub will be back to work.

hd0 nothing but your first harddisk i mean at which harddisk you had installed ubuntu(if single hd default value is zero )

---

### Post by nankura on 2011-08-13
i keep getting a strange error

> Setting up burg-common (1.98+20100623-1+maverick) ...
Setting up burg-pc (1.98+20100623-1+maverick) ...
Setting up burg-emu (1.98+20100623-1+maverick) ...
Setting up burg-themes-common (1.98+20100623-1) ...
Setting up burg-themes (1.98+20100623-1) ...
Setting up burg (1.98+20100623-1+maverick) ...
nankura@nankura-System-Product-Name:~$ sudo burg-install "(hd0)"
/usr/sbin/burg-probe: error: cannot find a device for /boot/burg (is /dev mounted?).
nankura@nankura-System-Product-Name:~$ sudo burg-install "/dev/sdc"
/usr/sbin/burg-probe: error: cannot find a device for /boot/burg (is /dev mounted?).
nankura@nankura-System-Product-Name:~$ sudo burg-install "/dev/sdc"


---

### Post by raja.genupula on 2011-08-13
hey man go with this 

 [http://ubuntuforums.org/showthread.php?t=1809658](http://ubuntuforums.org/showthread.php?t=1809658)

---

### Post by dcstar on 2011-08-13
> **nankura said:**
> i keep getting a strange error

```
sudo dpkg-reconfigure burg-pc
```

---

### Post by nankura on 2011-08-13
all fixed, thanks for the help guys :D

---

