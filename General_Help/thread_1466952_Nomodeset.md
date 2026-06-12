---
title: "Nomodeset"
date: 2010-04-30
forum: General Help
---

### Post by Okami on 2010-04-30
I have been using Lucid for some time now and have always needed to use nomodeset and later radeon.nomodeset=0 to able to boot, otherwise it is only a blank screen. Now after the final release I still have to boot with radeon.nomodeset=0! I don't know whats wrong and I don't even know what this nomodeset does. I hope someone can help me =)

Thanks in advance!

---

### Post by Groodles on 2010-04-30
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

Does this answer your questions?

---

### Post by clhsharky on 2010-04-30
HI Okami


Lucid is KMS 'kernel mode setting' by default, goggle for more info.
'radeon.nomodeset=0' will set radeon in UMS 'user mode setting' user space, the same with nomodeset.
KMS is the new way and has many advantages, including Plymouth.
Hope that helps some.

Sharky

---

### Post by Okami on 2010-04-30
Thank you both!

---

### Post by Okami on 2010-05-01
Two more questions...
The wiki says radeon KMS is work in progress so I tried using radeon.modeset=1 but it doesn't work =( By using modeset=0, does it affect the graphic cards performance? Is there a way to get i to work?

I have a radeon xpress 1250 card (integrated motherboard) and it seems it should be drivers available for linux from ATI, but nothing appears under "hardware drivers" in Ubuntu.

Thanks in advance!

---

### Post by Darent on 2010-05-02
I have the same problem with a radeon x1300. I thought it was a problem whit the beta versions but it's stil in the release...

The only way to boot normaly is deactivating it with the nomodeset. Also, there are some tutorials if you goole it to deactivate it always (changing the grub configuration so you don't need to type "nomodeset" everytime you boot)

Whitout the kms the only diference i see is that the capacities of the graphic card doesn't fully work until you log on the desktop (so you canot see a fade out after the boot to the login screen, the change betwen tty's and X are not so cool... things like that) but it's not a feature so important to loose the compiz xD I don't mind if my card works at kernel level, but it's a shame loose all 3D capabilities at user level.

I wish they solve this in the future for the radeno... i have a little netbook with another graphic card and the kms works perfectly... 

P.D. Excuse my english, as you can see it's not my native language...

---

