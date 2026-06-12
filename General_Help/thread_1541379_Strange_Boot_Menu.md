---
title: "Strange Boot Menu"
date: 2010-07-29
forum: General Help
---

### Post by mdmorash on 2010-07-29
I had an odd thing occur after a fresh install of Ubuntu 10.04. I installed Windows 7 on its partition, and all went fine. Then I installed Ubuntu on its partition and everything was as it should be. Then I did the Ubuntu updates and now my boot window looks like this ... 

Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (recovery mode)
Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (recovery mode)
Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (recovery mode)
Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (recovery mode)
memory test (memtest86+)
memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)

I can click on any of the Ubuntu logins and it takes me to the same place. My questions is has anybody seen this before, and how do I fix it?

Thanks for any help...

---

### Post by dino99 on 2010-07-29
never had this issue but in a console (ctrl+alt+f2):

sudo grub-mkconfig
sudo update-grub

sudo apt-get install -f

---

### Post by Rubi1200 on 2010-07-29
Can you still boot into Ubuntu and get to the desktop?
 
GRUB keeps a record of previous kernel versions, but this seems a bit odd.
 
If you go to Synaptic and search for linux image and linux headers you can see the different kernel versions and delete those you don't want or need.
 
Just make sure not to get rid of the most recent version!

---

### Post by mdmorash on 2010-07-29
I can click on any one of them and it takes me to the same desktop ... and the desktop functions normally.

---

### Post by Rubi1200 on 2010-07-29
Ok, boot using the most recent image, meaning the first one in the list, and then from the terminal run
 
```
sudo update-grub
```
 
Reboot and let us know what happens.

---

### Post by mdmorash on 2010-07-29
Okay, I did the update and now it reads like this ...

Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (recovery mode)
Ubuntu, with Linux 2.6.32-23-generic
Ubuntu, with Linux 2.6.32-23-generic (recovery mode)
Ubuntu, with Linux 2.6.32-22-generic
Ubuntu, with Linux 2.6.32-22-generic (recovery mode)
Ubuntu, with Linux 2.6.32-21-generic
Ubuntu, with Linux 2.6.32-21-generic (recovery mode)
memory test (memtest86+)
memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)

---

### Post by Rubi1200 on 2010-07-29
> **mdmorash said:**
> Okay, I did the update and now it reads like this ...
 
Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (recovery mode)
Ubuntu, with Linux 2.6.32-23-generic
Ubuntu, with Linux 2.6.32-23-generic (recovery mode)
Ubuntu, with Linux 2.6.32-22-generic
Ubuntu, with Linux 2.6.32-22-generic (recovery mode)
Ubuntu, with Linux 2.6.32-21-generic
Ubuntu, with Linux 2.6.32-21-generic (recovery mode)
memory test (memtest86+)
memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)
 
Ok, this makes more sense. You have previous kernel versions in the GRUB menu. As I suggested before, you can remove all but the most recent. However, many people keep at least one extra version in case an update breaks something.
 
Using Synaptic search for linux image and linux headers; there will be 3 files for each kernel version to delete. I suggest you keep 2.6.32-24 and 2.6.32-23

---

### Post by mdmorash on 2010-07-29
Okay, I'll do that. Thanks very much for the help.

---

### Post by mdmorash on 2010-07-29
Success, now it reads like this...

Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (recovery mode)
Ubuntu, with Linux 2.6.32-23-generic
Ubuntu, with Linux 2.6.32-23-generic (recovery mode)
memory test (memtest86+)
memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)

Thanks again for the help!

---

