---
title: "Dual boot Ubuntu 10.04 and Windows"
date: 2010-07-02
forum: General Help
---

### Post by digitography on 2010-07-02
Complete Linux noob so please be kind
Before I get flamed I would like to say I have followed other similar threads to no avail.

I installed Ubuntu onto a PC already running winXP, so far so good, the default boot is Ubuntu, this is fine for me, but others use the computer who it is not fine for.

I want to boot XP first, however the instructions I found instructed to edit the menu.lst file in the boot/grub folder.

There was no menu.lst file in the folder.

All the threads I found for this issue were for older version of Ubuntu, is 10.04 different?

Any useful answers are welcome.

---

### Post by Rubi1200 on 2010-07-02
> **digitography said:**
> Complete Linux noob so please be kind
Before I get flamed I would like to say I have followed other similar threads to no avail.

I installed Ubuntu onto a PC already running winXP, so far so good, the default boot is Ubuntu, this is fine for me, but others use the computer who it is not fine for.

I want to boot XP first, however the instructions I found instructed to edit the menu.lst file in the boot/grub folder.

There was no menu.lst file in the folder.

All the threads I found for this issue were for older version of Ubuntu, is 10.04 different?

Any useful answers are welcome.

Older versions of Ubuntu used GRUB-legacy. The current version (10.04) uses GRUB2, so yes the configuration files are different and are found in different places.

These links should provide the information you need, but feel free to post additional questions if you are unsure about anything and BEFORE you do anything please.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2](https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by 73ckn797 on 2010-07-02
> **digitography said:**
> Complete Linux noob so please be kind
Before I get flamed I would like to say I have followed other similar threads to no avail.

I installed Ubuntu onto a PC already running winXP, so far so good, the default boot is Ubuntu, this is fine for me, but others use the computer who it is not fine for.

I want to boot XP first, however the instructions I found instructed to edit the menu.lst file in the boot/grub folder.

There was no menu.lst file in the folder.

All the threads I found for this issue were for older version of Ubuntu, is 10.04 different?

Any useful answers are welcome.

Go to Synaptic Package Manager and install "startupmanager". Using that you can easily designate the default start up OS. It is a simple graphical way to accomplish what you are wanting.

---

### Post by digitography on 2010-07-02
Many thanks for both responses, which were both immensely informative and helpful.
I was able to load the startup manager, and now the computer boots into Windows by default.

Thanks again.

---

### Post by 73ckn797 on 2010-07-02
> **digitography said:**
> Many thanks for both responses, which were both immensely informative and helpful.
I was able to load the startup manager, and now the computer boots into Windows by default.

Thanks again.

Good deal. 

Use the Thread Tools at the top of the page and you can mark this as SOLVED. Others will be helped also.

---

### Post by digitography on 2010-07-02
Marked as Solved.

Loving Ubuntu :D

---

