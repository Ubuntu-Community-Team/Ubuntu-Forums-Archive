---
title: "wubi and Lubuntu 11.10 beta2"
date: 2011-09-23
forum: General Help
---

### Post by SleepySheep on 2011-09-23
I used to install **Lubuntu **using **wubi **when its version is still 10.10

Just repalce "X:\ubuntu\installation.iso" with ISO of Lubuntu and restart :lolflag:

Now I download Lubuntu **11.10** beta2 and I find **wubi** is included of ISO, but it doesn't support Lubuntu yet. (Ubuntu, Kubuntu, Xubuntu and Mythbuntu only)

So I'm gonna do same thing again. However, installation.iso does **not** exist any more. 

Any suggestions? Thx

---

### Post by bcbc on 2011-09-23
That's a good trick.

With 11.10 they are doing away with the '2 stage' installation. So wubi downloads an installed image (i386.tar.xz or amd64.tar.xz) and splats it on the virtual disk. After the windows install stage, it boots the new image directly and just adds the new user, creates the grub.cfg and the initrd.img.

Right now wubi 11.10 ALWAYS downloads the image, but this has been registered as a [bug]("https://bugs.launchpad.net/wubi/+bug/842397") - otherwise offline installs are no longer possible. Once they fix that you should be back in business.

---

### Post by SleepySheep on 2011-09-23
> **bcbc said:**
> That's a good trick.

With 11.10 they are doing away with the '2 stage' installation. So wubi downloads an installed image (i386.tar.xz or amd64.tar.xz) and splats it on the virtual disk. After the windows install stage, it boots the new image directly and just adds the new user, creates the grub.cfg and the initrd.img.

Right now wubi 11.10 ALWAYS downloads the image, but this has been registered as a [bug]("https://bugs.launchpad.net/wubi/+bug/842397") - otherwise offline installs are no longer possible. Once they fix that you should be back in business.

Thx. I hope wubi will support Lubuntu installation at that time :P

---

### Post by bcbc on 2011-09-23
> **SleepySheep said:**
> Thx. I hope wubi will support Lubuntu installation at that time :P

I haven't seen anything to indicate that Wubi will support Lubuntu in 11.10 :(
[http://ubuntuforums.org/showpost.php?p=11207214&postcount=314](http://ubuntuforums.org/showpost.php?p=11207214&postcount=314)

---

### Post by bcbc on 2011-09-24
If you refer to that bug I linked to - I have found there is a workaround that will make wubi install using the old 2 stage method - place the Ubuntu CD ISO on the root of a 'drive' before running wubi.exe. (Either use the latest daily-live Oneiric desktop CD ISO or run while not connected to the internet - you'll still need an oneiric desktop cd iso either way)

Then you can copy over your lubuntu image before rebooting.

---

