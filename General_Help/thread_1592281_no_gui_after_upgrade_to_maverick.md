---
title: "no gui after upgrade to maverick"
date: 2010-10-10
forum: General Help
---

### Post by Jotomicron on 2010-10-10
Hello everyone. Today I upgraded my Lucid to Maverick. After upgrading, from "update-manager -d", I tried a couple of new programs (games, actually) and re-enabled the third party repositories. I don't have exotic things, just google chrome, transmission beta, and some more of this sort...

After rebooting, the system enters in terminal instead of the regular gui. I tried to search online for possible solutions, but none worked. I tried 

(1) startx
output: fatal server error, no screen found.

(2) sudo service gdm stop; sudo service gdm start
Output: gdm start/running process 1265

(3) removing the option nomodeset from the boot. To do this I edited /etc/default/grub, the line with the GRUB_CMDLINE_LINUX and ran grub-mkconfig. After a reboot, the computer returned to the terminal.

(4) some even suggested removing /etc/X11/xorg.conf, but I don't have that file...

I have an acer timeline with initial hardware. I don't know which graphics card it has, if any... I really need to get my computer running, and I was looking for suggestions before reinstalling 10.04. Any help is appreciated! 

Thanks

---

### Post by Jotomicron on 2010-10-10
Apparently the problem was the lack of the xorg.conf file. I did have a xorg.conf.failsafe file, which I renamed to xorg.conf. Now I have a graphical environment, but the resolution is all wrong, and I can't change it. Besides, I don't think the system is recognizing the graphics card (which, I have learnt, is an Intel Mobile 4 series).

Can anyone help, please?
Thanks :)

---

### Post by borth92 on 2010-10-10
you need to install the graphics driver...if you can get to the desktop use system>administration>hardware drivers

---

### Post by Jotomicron on 2010-10-10
System > Administration > Additional Drivers tells me:
"No proprietary drivers are in use on this system."

---

### Post by Jotomicron on 2010-10-10
Apparently the solution is in xorg.conf.

I had:

```
Section "Device"
  Identifier "Configured Video Device"
  Driver "vesa"
EndSection
```

and simply changed the **vesa** to **intel**.

The resolution is correct again, and extra visual effects (those in Compiz) work too. I believe my problem is solved.

Thanks for your help, borth92 :)

---

