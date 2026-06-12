---
title: "How to change Grub2 themes"
date: 2009-07-22
forum: General Help
---

### Post by dwally89 on 2009-07-22
Hi,

I install Grub2 today, successfully, and downloaded some themes from [http://grub.gibibit.com/Themes](http://grub.gibibit.com/Themes) and ran the provided installation script, and the following message came up:

```
Usage: ./install DESTDIR
This will install the themes to DESTDIR/

```

And that was it... how to I apply the themes?

Thanks

---

### Post by doas777 on 2009-07-22
I usually use startup-manager to configure grub and usplash. it is in the repos

---

### Post by dwally89 on 2009-07-22
Isn't that only for grub 1?

---

### Post by kogger on 2009-07-22
Technically startup-manager is supposed to work for grub2, but the developer did say he was scrapping support for grub2 in order to build another version from scratch specifically targeted for it.

Do those themes work for grub2? Let me know if you can get it to work without breaking something.

---

### Post by dwally89 on 2009-07-22
Those themes do work for Grub2, if only I knew how to apply them... grr

---

### Post by kogger on 2009-07-22
[This page](https://wiki.ubuntu.com/Grub2#Theming) says theming is not yet supported in grub2. =\

---

### Post by dwally89 on 2009-07-22
So themes exist, they just can't be used yet??? Does that make any sense?

---

### Post by kogger on 2009-07-22
I think the existing themes are designed primarily to work with a graphical version of grub legacy. I'm happy with just a splash image for the moment, though.

---

### Post by dwally89 on 2009-07-22
Hmm the splash images are nice, but after seeing the screenshots on the website, was kind of disappointed.

Never mind, I guess we'll just have to wait.

---

### Post by kogger on 2009-07-22
You can use any image as a splash image. I have a GIMP-edited old-photo-style picture of lego construction workers. =P

---

### Post by al0x on 2009-12-20
I know this one is old, but you haven't even installed the themes...
try this code to install the themes in /boot/themes/:
```

./install /boot/themes/

```
after that it normally shows something like this:
```

sending incremental file list
...[lots of filenames]...
sent 1497408 bytes  received 1844 bytes  2998504.00 bytes/sec
total size is 1491017  speedup is 0.99

```
but I don't know how to apply them...

oh and sry for my bad english xP

greetz, al0x

---

### Post by jjsm586 on 2010-11-07
I tryed them with Arch Linux but they did not worked... They made my pc reboot in an endless loop.. you copy the files to /boot/grub/themes/ then you edit /etc/default/grub add a line GRUB_THEME="path to them" for example to add the winter theme you woul add the line GRUB_THEME=/boot/grub/themes/winter/theme.txt and don't forget to run update-grub after your done editing /etc/default/grub I hope this works for you...

---

