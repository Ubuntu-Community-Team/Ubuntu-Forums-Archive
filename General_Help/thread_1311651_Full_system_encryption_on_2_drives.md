---
title: "Full system encryption on 2 drives"
date: 2009-11-02
forum: General Help
---

### Post by SubNetMask on 2009-11-02
I have Windows Vista installed on a 500GB hard drive, and Ubuntu 8.10 installed on another 500GB hard drive, they are both in the same computer. Now, I want to fully encrypt both drives, from windows I can just use TrueCrypt, but if I do full system encryption will it overwrite the GRUB bootloader? And if I do it from Ubuntu how Will Windows boot if GRUB is the bootloader and the drive needs to be decrypted before the bootloader can be accessed. 

I would prefer not having to reinstall Ubuntu to do a full system encryption. I'm just wondering before I try this and overwrite the encryption headers, is it possible to have full system encryption on 2 HDDs and still be able to dualboot?

---

### Post by P4man on 2009-11-02
> **SubNetMask said:**
> I have Windows Vista installed on a 500GB hard drive, and Ubuntu 8.10 installed on another 500GB hard drive, they are both in the same computer. Now, I want to fully encrypt both drives, from windows I can just use TrueCrypt, but if I do full system encryption will it overwrite the GRUB bootloader? 

I dont think so. The bootloader (stage1) sits on the Master Boot Record (MBR) its not part of a partition, encrypting the drive shouldnt touch it.

> 
And if I do it from Ubuntu how Will Windows boot if GRUB is the bootloader and the drive needs to be decrypted before the bootloader can be accessed. 

Not only windows will have trouble booting, ubuntu too. I think you have to create a separate boot partition to put grub on (stage 2) otherwise grub would not be able to load at all. That said, I dont see the point of encrypting anything other than your /home partition.

---

### Post by SubNetMask on 2009-11-02
> **P4man said:**
> 
Not only windows will have trouble booting, ubuntu too. I think you have to create a separate boot partition to put grub on (stage 2) otherwise grub would not be able to load at all. 


Oh okay. I'll read up on that, thanks.

Just don't want to mess anything up since I have 800GB of data and I'd rather not lose half of it encrypting the drives.

---

