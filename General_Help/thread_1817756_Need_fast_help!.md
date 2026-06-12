---
title: "Need fast help!"
date: 2011-08-03
forum: General Help
---

### Post by Vizuh on 2011-08-03
My Ubuntu partition is corrupt. I was installing upgrades and the power supply on my PC was knocked out, now it won't boot. I've tried running the repair option at startup with no luck.

I was about to install Windows XP and then I remembered that all of my holiday pictures were on the Ubuntu partition and it would kill me to lose them all.

Please help, fast.

---

### Post by akand074 on 2011-08-03
Grab an Ubuntu cd, boot into the live disk and mount your drive. Just copy/paste all your files into a USB/External hard drive. 

You should really have more descriptive titles.

---

### Post by mihalybaci on 2011-08-03
You could try booting a Live CD or Live USB and click 'Try Ubuntu' (DO NOT INSTALL!). Once it loads, mount the hard drive where your pictures are. Then, hopefully, you'll be able to navigate to your pictures (and anything else) and back them up on CDs, DVDs, or an external hard drive. Then you can try to fix the problem knowing you have a backup copy of everything.

---

### Post by zealibib slaughter on 2011-08-03
You can use a ubuntu cd for a live session and recover all your documents.

---

### Post by Vizuh on 2011-08-03
> **akand074 said:**
> Grab an Ubuntu cd, boot into the live disk and mount your drive. Just copy/paste all your files into a USB/External hard drive. 

You should really have more descriptive titles.

Sorry and thanks, will give this a shot.

> **mihalybaci said:**
> You could try booting a Live CD or Live USB and click 'Try Ubuntu' (DO NOT INSTALL!). Once it loads, mount the hard drive where your pictures are. Then, hopefully, you'll be able to navigate to your pictures (and anything else) and back them up on CDs, DVDs, or an external hard drive. Then you can try to fix the problem knowing you have a backup copy of everything.

Thanks for the reply, gonna go try this now ;)

> **zealibib slaughter said:**
> You can use a ubuntu cd for a live session and recover all your documents.

Thanks mate :)

---

### Post by Vizuh on 2011-08-03
> **akand074 said:**
> Grab an Ubuntu cd, boot into the live disk and mount your drive. Just copy/paste all your files into a USB/External hard drive. 

You should really have more descriptive titles.

> **mihalybaci said:**
> You could try booting a Live CD or Live USB and click 'Try Ubuntu' (DO NOT INSTALL!). Once it loads, mount the hard drive where your pictures are. Then, hopefully, you'll be able to navigate to your pictures (and anything else) and back them up on CDs, DVDs, or an external hard drive. Then you can try to fix the problem knowing you have a backup copy of everything.

> **zealibib slaughter said:**
> You can use a ubuntu cd for a live session and recover all your documents.


I'm currently running Ubuntu off of my USB stick. I've found the partition I have it installed one and i'm trying to access the Home folder. It says I don't have the neccesary permissions :/

---

### Post by westie457 on 2011-08-03
> **Vizuh said:**
> I'm currently running Ubuntu off of my USB stick. I've found the partition I have it installed one and i'm trying to access the Home folder. It says I don't have the neccesary permissions :/

```
gksudo nautilus
``` in a terminal should allow you to copy & paste with or without permissions.

---

### Post by Vizuh on 2011-08-03
> **westie457 said:**
> ```
gksudo nautilus
``` in a terminal should allow you to copy & paste with or without permissions.

No luck. When I go into my Home > James folder, I only get 2 files - README.txt and Access-your-private-desktop.desktop :S

---

### Post by zealibib slaughter on 2011-08-03
Ok its encrypted.  here is the ubuntu help page for that [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)
Its a little complicated but well explained how to access it with a live cd

---

### Post by Vizuh on 2011-08-03
Is there any way to view the Ubuntu partition in Windows 7?

---

### Post by Vizuh on 2011-08-04
Anyone?

---

### Post by DrScum on 2011-08-04
Depending what the file system of your ubuntu partition is, chances are slim that you'll be able to see and mount it in win7. However, I don't know the details about file system compatibility for win7.

My suggestion is to stay on the live CD path (I always use a puppy linux live CD for this kind of work) to get to your data.

---

### Post by Vizuh on 2011-08-04
> **DrScum said:**
> Depending what the file system of your ubuntu partition is, chances are slim that you'll be able to see and mount it in win7. However, I don't know the details about file system compatibility for win7.

My suggestion is to stay on the live CD path (I always use a puppy linux live CD for this kind of work) to get to your data.

Not really sure what you mean, i'm pretty new to Ubuntu. Is there any sort of repair disc for Ubuntu 11.04?

---

### Post by dino99 on 2011-08-04
you are "new" as you have said but already use complicated/unstable settings (encrypted folder) and ask for "fast help" meaning "you panic"

well its the way noobs fails then they learn how to work in a secure way: if you dont understand complicated things, then dont use them.

that said you can check for errors in the partitions and try to fix them:

sudo shutdown -r now 
(will force a fsck on next boot)

then try again the recovery mode to repair the packages.

---

### Post by westie457 on 2011-08-04
> **Vizuh said:**
> Is there any way to view the Ubuntu partition in Windows 7?

This allows read and write to EXT partitions from Windows. [http://www.ext2fsd.com/](http://www.ext2fsd.com/)

---

