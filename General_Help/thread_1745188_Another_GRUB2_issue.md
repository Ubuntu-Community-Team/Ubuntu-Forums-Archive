---
title: "Another GRUB2 issue"
date: 2011-04-30
forum: General Help
---

### Post by kpeoples86 on 2011-04-30
I am working on a computer where the owner is running Windows 7 and 10.10.  Windows 7 was lost when I turned it on on the GRUB list.  I tried to update-grub2 and Windows 7 never showed up so I found the partition that it was on and manually added it to the grub.cfg file and it worked but every time grub updates Windows goes away again.

I would like to find a way to make Windows 7 show up after a grub update or prevent GRUB from updating at all.

---

### Post by drs305 on 2011-04-30
kpeoples86,

Welcome to the Ubuntu forums.

I can give you the commands to 'disable' update-grub but would prefer to fix it if possible. Do you know if *os-prober* is installed and working. It isn't installed by default on some distros, such as lubuntu.

You can check by trying to run:
```
sudo os-prober
```
Does it run, and if so, does it see Windows?

You can also check the /boot/grub/grub.cfg file and see if it contains a "### BEGIN /etc/grub.d/30_os-prober ###" section. This is where Grub should be placing the Windows entry.

If you think you need to install/reinstall os-prober:```

sudo apt-get install os-prober
or 
sudo apt-get install --reinstall os-prober
```

If the above doesn't solve it, rather than disabling update-grub I'd recommend placing the Windows entry you manually created in /etc/grub.d/40_custom. Just place it below the existing lines, save the file, and update-grub. It will appear in the grub menu *and remain there during grub updates*.

---

### Post by idoitprone on 2011-04-30
edit: the guy above me already said all the options

---

### Post by kpeoples86 on 2011-04-30
> **drs305 said:**
> 
If you think you need to install/reinstall os-prober:```

sudo apt-get install os-prober
or 
sudo apt-get install --reinstall os-prober
```If the above doesn't solve it, rather than disabling update-grub I'd recommend placing the Windows entry you manually created in /etc/grub.d/40_custom. Just place it below the existing lines, save the file, and update-grub. It will appear in the grub menu.


I did not have os-prober installed and as soon as I installed it and re-updated grub2 it found it.

Thank you so much

---

### Post by drs305 on 2011-04-30
> **kpeoples86 said:**
> I did not have os-prober installed and as soon as I installed it and re-updated grub2 it found it.


:-)

If it wasn't Lubuntu, would you mind telling us which OS didn't have it installed. *os-prober* IMO is a pretty basic building block for Grub2 and I'm disappointed it isn't always installed by default. 

Us 'helpers' have to keep this possibility in mind when trying to offer solutions, so if there are other distros besides Lubuntu we'd appreciate the heads up.

Happy Ubuntu-ing !

---

### Post by kpeoples86 on 2011-04-30
It was not installed by me I am just helping a friend out.  It is the basic version of Ubuntu 10.10 Maverick Meerkat 64-bit.  I don't know why he didn't have os-prober on it by default.  It was installed on an ASUS laptop if that helps at all.

Other then that I am not sure what the issue was.

---

