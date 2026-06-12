---
title: "grub mix-up"
date: 2011-06-03
forum: General Help
---

### Post by gandaran on 2011-06-03
so I have installed kubuntu 11.04 on a separate partition alongside ubuntu 11.04 and windows 7, kubuntu replaced the ubuntu grub, thats okay, but I want the ubuntu grub back so I can use grub-customizer to set which boots first, I have run the update-grub command from ubuntu
```
mfp@PC:~$ sudo update-grub
[sudo] password for mfp: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Ubuntu 11.04 (11.04) on /dev/sda7
done
mfp@PC:~$ 
``` 
(Ubuntu 11.04 on /dev/sda7 is actually kubuntu)
but I still get the kubuntu grub with the blue background and grub-customizer doesn't work on it, I even tried using the rescatux live cd with no luck to restore the ubuntu grub, so how do I bring back the ubuntu grub?
or which file do I edit and how on the kubuntu grub to boot ubuntu first place?

---

### Post by Rubi1200 on 2011-06-03
Easiest method in my opinion would be to reinstall GRUB to the Ubuntu partition and let it control booting again:
[https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files](https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files)

Since you are using 11.04 make sure you use the command specific for that to reinstall GRUB to the MBR.

---

### Post by drs305 on 2011-06-03
Follow Rubi1200's recommendation if you are in Kubuntu. If you have already rebooted and are running the system whose Grub you want to control the boot (Ubuntu), you can just:```

sudo grub-install /dev/sda
```

Added: As you have found, 'update-grub' will update that system's grub menu, but it doesn't necessarily update the actual boot menu you see unless that Grub happens to be the one controlling things. The one controlling the boot will list it's kernel first on the displayed menu unless you have reordered things.

---

### Post by gandaran on 2011-06-03
thanks for the replies, I got the ubuntu grub back, tried again with rescatux live-usb  and this time it did restore the grub.

---

### Post by Rubi1200 on 2011-06-03
Excellent! Glad you got things sorted out :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

