---
title: "Puppy live CD to install on USB results in failure to boot from HDD?"
date: 2009-09-21
forum: General Help
---

### Post by omskates on 2009-09-21
HI,
My desktop machine runs one OS=Ubuntu Jaunty
I had booted a live Teenpup 2009 and used universal installer to install it to a USB flash drive. Then I used Grub bootloader config simple >Standard >entered the flash device and Selected "MBR" OK then unmounted and removed flash drive. Rebooted choosing my HDD and Ubuntu will not boot now & displays "Error 21" Any files copied from puppy halting my Ubuntu boot?
Thankyou

---

### Post by omskates on 2009-09-21
I decided to restore grub and now I'm booting fine into Ubuntu:).  Still unsure why the change occured:confused:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

---

### Post by mike555 on 2009-09-21
the change was because you told puppy to install boot loader to mbr , but pulled out the USB ......... if grub can't find USB it will error ......... probably would have worked if you left USB in ............. it would have been better to install puppy's bootloader to the USB , then push a button (ESC I think )when starting to pick the USB ..............

---

