---
title: "Plymouth displays for about 1-2 seconds then shows login screen"
date: 2010-10-28
forum: General Help
---

### Post by RJ12 on 2010-10-28
Well this problem has been here since Lucid. When I start up my computer and select Ubuntu, I get a blinking underscore for about most of the start up time for Ubuntu. Then It quickly shows the nice Ubuntu Loading Screen (Plymouth) for about two seconds, then it gets to the login screen. Is there a way to fix this? If it helps, I am using the Open Source ATI drivers, I believe the open drivers are called "radeon".


Thanks!:KS

---

### Post by mister_playboy on 2010-10-28
```
sudo echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u
```

The first step creates a file called splash containing a single line FRAMEBUFFER=y and puts the file in the /etc/initramfs-tools/conf.d folder.  If you encounter an error, try doing each part separately.

Booting may take a bit more time, but it will look much better. :)

---

### Post by RJ12 on 2010-10-29
> **mister_playboy said:**
> ```
sudo echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u
```

The first step creates a file called splash containing a single line FRAMEBUFFER=y and puts the file in the /etc/initramfs-tools/conf.d folder.  If you encounter an error, try doing each part separately.

Booting may take a bit more time, but it will look much better. :)

Before I do this, is it reversible? I would hate to ruin this install because of trying to make my bootup prettier.

---

### Post by mister_playboy on 2010-10-29
Yes, it's reversible.  You can undo it with this command: ```
sudo rm /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u
```

---

### Post by coffeecat on 2010-10-29
> **mister_playboy said:**
> ```
sudo echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u
```

The first command doesn't work because the sudo elevation only works for the echo; it doesn't carry through to the bash redirect. You need:

```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
```Or...

```
gksudo gedit /etc/initramfs-tools/conf.d/splash
```... and type  the 'FRAMEBUFFER=y' into the empty file and save.

---

### Post by RJ12 on 2010-10-29
Thanks guys! It worked :)


-Solved!!

---

