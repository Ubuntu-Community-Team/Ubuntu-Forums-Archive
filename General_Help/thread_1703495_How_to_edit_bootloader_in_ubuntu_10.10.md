---
title: "How to edit bootloader in ubuntu 10.10"
date: 2011-03-09
forum: General Help
---

### Post by jp07025 on 2011-03-09
Hello,

How does bootloader edit in ubuntu 10.10? For example, I would like to select default boot windows instead of ubuntu.

Thank you.

---

### Post by oldos2er on 2011-03-09
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

There's also a GUI program 'Grub customizer': [https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)

---

### Post by JRV on 2011-03-09
Change "GRUB_DEFAULT=0" in /etc/default/grub.

0=line one, 1=line two 

just point to the line for Windows.

Use this command to edit:
```
gksudo gedit /etc/default/grub
```

---

### Post by stinkeye on 2011-03-09
This command when run in the terminal will show you
the number to use with JRV's advice.
```
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
```

and after you have edited /etc/default/grub, run
```
sudo update-grub
```

---

### Post by JRV on 2011-03-10
> **stinkeye said:**
> 
and after you have edited /etc/default/grub, run
```
sudo update-grub
```

Thanks for mentioning update-grub, that slipped my mind.

---

