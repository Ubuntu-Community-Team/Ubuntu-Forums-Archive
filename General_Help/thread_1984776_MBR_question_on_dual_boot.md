---
title: "MBR question on dual boot"
date: 2012-05-22
forum: General Help
---

### Post by Yaj on 2012-05-22
Appreciate a link or tips on the following:
I have read somewhere that a "clean" way to implement dual boot on a laptop which shipped with Windows 7 on the primary drive, with an added secondary dedicated drive for Ubuntu Linux is the following:
1. Remove primary hard drive (with Windows), screw in the blank hard drive in place of the primary HD. 
2. Install Ubuntu in the new primary (while the Windows drive is no longer attached to the laptop).
3. Take out the Ubuntu hard drive from its primary location, put back the Windows drive, and put in the Ubunty drive in its secondary position.
4. Then do what to make the Windows MBR be in control?

Thanks in advance

---

### Post by mikewhatever on 2012-05-22
You'll need to use a boot manager called [EasyBCD]("http://neosmart.net/EasyBCD/"). Check out their User Guide for more info.

Alternatively, just boot from the HDD with Ubuntu installed.

---

### Post by ManiacDan on 2012-05-22
If they're two separate drives, you can just hit esc during boot (or whatever) to access the motherboard's boot menu and boot to the other drive.

Note that if you've installed win7ultimate and enabled drive encryption, you will NOT be able to alter the MBR nor will you be able to put any non-windows filesystems on that drive.

---

### Post by Yaj on 2012-05-22
@ManiacDan - this option of using the motherboard's boot menu, does it require going through the same process, i.e. remove the current primary HDD (Windows), put the new HDD, install Linux, then remove it etc. *WITHOUT* the use of EasyBCD?

---

### Post by wilee-nilee on 2012-05-22
> **Yaj said:**
> Appreciate a link or tips on the following:
I have read somewhere that a "clean" way to implement dual boot on a laptop which shipped with Windows 7 on the primary drive, with an added secondary dedicated drive for Ubuntu Linux is the following:
1. Remove primary hard drive (with Windows), screw in the blank hard drive in place of the primary HD. 
2. Install Ubuntu in the new primary (while the Windows drive is no longer attached to the laptop).
3. Take out the Ubuntu hard drive from its primary location, put back the Windows drive, and put in the Ubunty drive in its secondary position.
4. Then do what to make the Windows MBR be in control?

Thanks in advance

You just want to make sure that your install and the grub bootloader goes to tha HD, grub to its mbr.

On the install use the something other option, the custom install, and check the dropdown as to where grub is pointed.

Some suggest a HD removal this is not needed, unless you are like extra worried. Nor is easybcd needed.

Set the HD with Ubuntu as the first read and you will have the grub menu to choose ubuntu or windows, and if you remove the Ubuntu change the drive to being the first read to boot straight in.

---

### Post by mikewhatever on 2012-05-23
> **Yaj said:**
> @ManiacDan - this option of using the motherboard's boot menu, does it require going through the same process, i.e. remove the current primary HDD (Windows), put the new HDD, install Linux, then remove it etc. *WITHOUT* the use of EasyBCD?

All this moving of hdds is not really required, it's just a precaution for those who don't want the Windows MBR overwritten. Ubuntu installer will overwrite the MBR of the first HDD by default, unless the user selects a different location. So, taking the HDD with Windows out makes sure that there is no way to overwrite its MBR.

I think that taking out the HDD with Windows would be sufficient. The installer shouldn't care in which bay the target HDD is.

---

### Post by ManiacDan on 2012-05-23
Mike is right, the point of swapping drives is to make sure you don't accidentally wipe the whole thing.

Most motherboards have an option where you can hit a key (esc, f12, f11, etc) to access a quick boot menu, for booting off CDs or whatever.  if your motherboard has that, it should show you all the physical drives in the system.  You can just boot that way, in theory.  ymmv based on motherboard.

---

