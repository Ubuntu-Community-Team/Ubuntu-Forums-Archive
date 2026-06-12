---
title: "Dual Boot - Can't start xp"
date: 2010-12-20
forum: General Help
---

### Post by Alonsotron on 2010-12-20
I installed Ubuntu on my netbook alonside xp. The only problem is that when I start my computer, the boot menu only pops up for a split second and I cannot select "run windows xp". This is preventing me from usintg both OS'. Would anyone mine telling me how I can fix this?

---

### Post by unplugged23 on 2010-12-20
I would suggest 'spamming' the escape key as fast as possible while the computer is booting up, because I belive this stops the grub countdown. Then you should freely be able to choose how to boot.
If I remember correctly it is also possible to change how long the grub countdown takes before it boots into the default OS. ```
sudo vi /boot/grub/menu.lst
```

Good luck!

---

### Post by drs305 on 2010-12-20
Alonsotron,

Welcome to the Ubuntu forums.  :-)

If you are running the Grub 2 bootloader, which is the current default for Ubuntu, try holding down the SHIFT key as the computer boots. The menu may display.

If you don't have a Windows menu item:
Once it boots, you may need to run a command to make sure Windows is seen. Open a terminal (Applications, Accessories, Terminal) and type in:
```
sudo update-grub
```
It will ask for a password. Enter yours, but you won't see it. Windows should be included in the menu the next time you boot.

The links in my signature line explain Grub2. The "G2-Tasks" lists the more common things you might like to tweak on the Grub 2 menu.

---

