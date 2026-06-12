---
title: "How Can I Stop the Grub Menu from Appearing at Boot?"
date: 2011-08-06
forum: General Help
---

### Post by Joseph Schwenker on 2011-08-06
After some system updates, I now have the Grub menu appearing every time I boot my computer. Is there any way to disable it, or make it automatically boot whichever entry is selected by default? I only have one operating system installed, so there's not much of a point to having to press enter every time my computer starts up.

---

### Post by drs305 on 2011-08-06
If there is no other OS it shouldn't show, so it could be recording a recordfail event which triggers the menu display. Is there a timer countdown or does it remain displayed until you select an item?

I would first try to use 'Grub Customizer' to set the timeout to 0. Click the link "Customizer" in my signature line. It's a great GUI app that can tweak a lot of Grub 2 settings.

If you still can't hide it, please run the boot info script from the following site and post the contents of RESULTS.txt.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Joseph Schwenker on 2011-08-06
> **drs305 said:**
> If there is no other OS it shouldn't show, so it could be recording a recordfail event which triggers the menu display. Is there a timer countdown or does it remain displayed until you select an item?

I would first try to use 'Grub Customizer' to set the timeout to 0. Click the link "Customizer" in my signature line. It's a great GUI app that can tweak a lot of Grub 2 settings.

If you still can't hide it, please run the boot info script from the following site and post the contents of RESULTS.txt.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

There's a timer until it automatically boots the first item, which is the one I want. Can I just comment out the timer line or set it to zero with the following command?```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by drs305 on 2011-08-06
> **Joseph Schwenker said:**
> There's a timer until it automatically boots the first item, which is the one I want. Can I just comment out the timer line or set it to zero with the following command?```
gksudo gedit /boot/grub/menu.lst
```

We can be more certain if we see the RESULTS.txt, but if you haven't tried making any changes, you are using Grub 2 (*grub-install -v* will tell you - it would be Grub 1.98 or Grub 1.99), and you have no other OS's, you can edit the following file:
```
gksu gedit /etc/default/grub
```
Change the value of 10 to 0:
> GRUB_TIMEOUT=**10**
Save the file, then run the following to update the menu.
```
sudo update-grub
```

---

### Post by Joseph Schwenker on 2011-08-06
> **drs305 said:**
> We can be more certain if we see the RESULTS.txt, but if you haven't tried making any changes, you are using Grub 2 (*grub-install -v* will tell you - it would be Grub 1.98 or Grub 1.99), and you have no other OS's, you can edit the following file:
```
gksu gedit /etc/default/grub
```
Change the value of 10 to 0:

Save the file, then run the following to update the menu.
```
sudo update-grub
```

Thanks! Those commands seem to have run correctly. I'll reboot my computer shortly to see if this fixed the problem.

---

