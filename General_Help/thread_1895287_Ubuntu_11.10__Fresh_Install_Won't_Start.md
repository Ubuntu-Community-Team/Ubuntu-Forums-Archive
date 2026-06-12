---
title: "Ubuntu 11.10  Fresh Install Won't Start"
date: 2011-12-14
forum: General Help
---

### Post by larsjuh on 2011-12-14
Hello,

I've used dual boot before with wubi (without problems),

Now i wanted to install only ubuntu (no windows anymore)

And when i installed ubuntu i get "Error: hd0 out of disk", or sometimes i have to select a proper media device to boot (something like that)

I thought my boot loader was corrupt or so, so i did a BOOT repair which said it was successfully repaired, but i still have the same after rebooting...

The repair tool made a LOG:

[http://paste.ubuntu.com/770316/](http://paste.ubuntu.com/770316/)

I've installed ubuntu 11.10 like 5 times, but its the same every time.. i don't know what the problem is.

Help appreciated!

Greetings

---

### Post by comradeluigi on 2011-12-14
what is your computer model?

---

### Post by larsjuh on 2011-12-14
I have a samsung laptop (RC730) ([http://fauzanvs.blogspot.com/2011/10/samsung-rc730-s05de-notebook-review.html](http://fauzanvs.blogspot.com/2011/10/samsung-rc730-s05de-notebook-review.html))

With updated bios version.

And freshy installed SSD OCZ agility 3 120gb (also newest firmware)

---

### Post by BC59 on 2011-12-14
Wubi is not dual boot, it's just an installation through Windows.

To check if you can install Ubuntu, boot from the Disc or USB you are doing the installation and choose Try Ubuntu, instead of Install Ubuntu.

---

### Post by larsjuh on 2011-12-14
> **BC59 said:**
> Wubi is not dual boot, it's just an installation through Windows.

To check if you can install Ubuntu, boot from the Disc or USB you are doing the installation and choose Try Ubuntu, instead of Install Ubuntu.

Booting from the disc does work, and it does see my SSD drive, i can browse it too... =)

Everything works perfectly from the CD.

---

### Post by BC59 on 2011-12-14
I searched and this is a not so unusual problem.
Is related to the Grub boot.

Go here, it's the best guide available and try the solution on point .13 of the first post.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by larsjuh on 2011-12-14
reinstalling the grub loader didn't work.

I've changed AHCI settings in the BIOS to "auto" instead of AHCI enabled and now it does work!.

Thanks for your time.

---

