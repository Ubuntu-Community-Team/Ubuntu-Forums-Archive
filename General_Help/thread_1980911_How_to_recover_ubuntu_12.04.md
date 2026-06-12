---
title: "How to recover ubuntu 12.04"
date: 2012-05-16
forum: General Help
---

### Post by vishalnshekhar on 2012-05-16
i have ubuntu 12.04 and yesterday i try to install nvidia graphics and then gdm then after restart my screen become 4:3 then i remove gdm and we i try to restart i can't be able to reboot.
i try fix this problem by recovery mode then fail graphic mode i reconfigure my graphics mode but my problem is not solve
Is there any way to recover or re-install ubuntu without removing my software and data.
i also live usb created.

---

### Post by Los Frijoles on 2012-05-16
Honestly, the best bet is to re-install ubuntu in my opinion. I have had a few times where I did something that wasn't undoable and it broke everything. I have now ended up moving my home folder decrypted to a separate partition so that I can just re-install linux pretty easily without having to worry about recovering my files since they will stay safe in the separate partition.

I would load up the live CD, get an external hard drive, follow the guide for recovering your home folder if it is encrypted ([https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live_CD_method_of_opening_a_encrypted_home_directory)), copy everything in your home folder to the external hard drive, and then re-install ubuntu.

After installing you should carefully check all the hidden files that are placed in your home directory to make sure that you aren't overwriting any crucial settings when you place the backup that you stored in the external hard drive back on your partition.

---

