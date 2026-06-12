---
title: "Installed Ubuntu 9.10 then Windows XP"
date: 2010-03-09
forum: General Help
---

### Post by chrislynch8 on 2010-03-09
Hi,

SO I installed Ubuntu 9.10 nad then windows XP. Now I can only get into windows. I tried to re-install Grub on the linux partition but I get an error: Cannot Read `/grub/core.img`correctly

I followed the tutorial on this forum. I booted to my Ubunut CD, ran termainal, sudo fdisk -l, mounted my Linux partition and ran sudo grub-install --root-directory=/media/sda1 /dev/sda1. Which gave the error above.

How else can I fix this. Bearing in mind I cannot log into my Ubuntu system.

Rgds
Chris

---

### Post by roon on 2010-03-09
Use this howto ---> [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

If fail then report back wit the results and also try this link ---> [http://lmgtfy.com/?q=grub2+recover](http://lmgtfy.com/?q=grub2+recover)

---

### Post by ndefontenay on 2010-03-09
Windows is rather intolerant to any other OS and will require to be the only one existing to be installed.

So install windows first, keep some space for linux then install linux.

---

### Post by howefield on 2010-03-09
> **ndefontenay said:**
> Windows is rather intolerant to any other OS and will require to be the only one existing to be installed.

So install windows first, keep some space for linux then install linux.

It is "preferable" to install Windows first, but given that the OP hasn't, why would he want to reinstall both operating systems again, when the link roon gave should fix it in a couple of minutes ?

You're making life rather hard for him ;-)

---

