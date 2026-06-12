---
title: "Ubuntu doesn't runs in HD"
date: 2012-10-02
forum: General Help
---

### Post by sergi70 on 2012-10-02
Hi guys! I'm having troubles with ubuntu again. I have installed 12.04 LTS in my Toshiba Satellite from an USB stick (nomodeset, nolapic, acpi off) and it installed succefully. But when it boots up i just get an purple screen. What can i do? Thx so much.

---

### Post by wojox on 2012-10-02
Did you set  (nomodeset, nolapic, acpi off) again until you install your video driver?

---

### Post by sergi70 on 2012-10-02
> **wojox said:**
> Did you set  (nomodeset, nolapic, acpi off) again until you install your video driver?
I tryed with "E" key in GRUB, but when i try to boot with "F10" it gives me an error of Booting node 0 Processors #1 I  have heard something about updating BIOS,  but i don't want to do this, it scares my father and he doesn't wants to loose his laptop.

---

### Post by dino99 on 2012-10-02
you can try to boot without "splash" on the boot line. If that works, then watch your logs (/home/youruser/.xsession-errors (ctrl+h to unhide it, and into /var/log/).
Otherwise try booting in recovery mode. Note that you need some specific packages installed : toshset & fnfxd , but they should have been installed automatically).

More info can be found if you google around "ubuntu yourtoshmodel"

---

### Post by sergi70 on 2012-10-02
> **dino99 said:**
> you can try to boot without "splash" on the boot line. If that works, then watch your logs (/home/youruser/.xsession-errors (ctrl+h to unhide it, and into /var/log/).
Otherwise try booting in recovery mode. Note that you need some specific packages installed : toshset & fnfxd , but they should have been installed automatically).

More info can be found if you google around "ubuntu yourtoshmodel"
I tryed no splash and happens the same. Node 0... In recovery mode i just get an black screen with a slash. Anything more. What is happening? Really strange thing here.

---

### Post by dino99 on 2012-10-02
maybe you could log via :

  Alt+Ctrl+F1 while purple screen: can You login in text mode

Related "node" issue:
[http://askubuntu.com/questions/100721/ubuntu-11-10-64-bit-wont-start-after-i-upgrade-it-possible-procesor-problems](http://askubuntu.com/questions/100721/ubuntu-11-10-64-bit-wont-start-after-i-upgrade-it-possible-procesor-problems)

---

### Post by sergi70 on 2012-10-02
> **dino99 said:**
> maybe you could log via :

  Alt+Ctrl+F1 while purple screen: can You login in text mode

Related "node" issue:
[http://askubuntu.com/questions/100721/ubuntu-11-10-64-bit-wont-start-after-i-upgrade-it-possible-procesor-problems](http://askubuntu.com/questions/100721/ubuntu-11-10-64-bit-wont-start-after-i-upgrade-it-possible-procesor-problems)
I will try, but its a very strange problem, i have never had with older verisons like 10.04

---

