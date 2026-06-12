---
title: "delete ubuntu partiton"
date: 2010-06-11
forum: General Help
---

### Post by stubblepoo on 2010-06-11
if i was to format the ubuntu partition whilst in xp i wouldremove the grub menu too. would the pc then hang or boot automatically into xp. normally i would just do it and see what occurs but its my mums laptop now so i am not allowed to play aobut with it.
cheers

---

### Post by X-Windows on 2010-06-11
I don't believe a format would erase the grub, as that is in the BIOS not the hard drive. You should really learn to speak english before posting though (unless you are foreign of course), it is incredibly difficult to decipher what you are trying to do.

---

### Post by new_tolinux on 2010-06-11
[http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/](http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/)

Quite a clear howto to me. I suggest you use the XP CD.
> 
**Using Windows XP boot disk**

 Boot computer using Windows XP (Windows 2000)[COLOR=#6666CC] setup disc / CD / DVD[/COLOR]. Next, type the  following commands:
# fixmbr
# exit

---

### Post by new_tolinux on 2010-06-11
> **X-Windows said:**
> I don't believe a format would erase the grub, as that is in the BIOS not the hard drive. You should really learn to speak english before posting though (unless you are foreign of course), it is incredibly difficult to decipher what you are trying to do.
You're absolutely wrong. Grub has _nothing_ to do with the BIOS.

---

### Post by eriktheblu on 2010-06-11
if you have just the one EXT partition, it would eliminate your grub boot loader. Many will create a separate partition for /boot (~256 MB is more than enough) to avoid problems like that.

If you delete /boot, your hard disk's MBR will point to a non-existent boot loader. This will result in no OS booting.

To get around this, you need to redirect your MBR to the Windows partition. MS provides some tools to do that, and there are OSS programs as well.

---

### Post by eriktheblu on 2010-06-11
Recommendation: redirect your MBR *before* you format.

---

### Post by mikewhatever on 2010-06-11
> **X-Windows said:**
> I don't believe a format would erase the grub, as that is in the BIOS not the hard drive. You should really learn to speak english before posting though (unless you are foreign of course), it is incredibly difficult to decipher what you are trying to do.

No, Grub has nothing to do with the bios. A small portion of it is installed to the MBR of the hdd, and the rest is in /boot/grub on the Ubuntu partition. If Grub is used to boot both Ubuntu and Windows, and the Ubuntu partition is deleted, the remaining Windows will not boot.

---

### Post by JayKay3000 on 2010-06-11
deleted

---

### Post by X-Windows on 2010-06-11
> **new_tolinux said:**
> You're absolutely wrong. Grub has _nothing_ to do with the BIOS.

I stand corrected.

---

### Post by WorMzy on 2010-06-11
> **JayKay3000 said:**
> If you have installed ubuntu after XP then you should be ok as xp will still retain its boot loader. Installing the grub loader simply finds and adds windows to the list.

When you delete the ubuntu partition the loader will probably go with it. When you re-boot your computer it should default to the windows loader and boot straight into xp

I've done this on my xp and win 7 machines and it has always reverted back to the original boot loader when grub is gone.

You've either been rearranging your disk boot order in the BIOS or have magic powers. :P

When you install Ubuntu (and grub), it overwrites whatever is previously in the MBR. So if you install Ubuntu after Windows, grub will be installed to the MBR over the top of the Windows bootloader. When you remove Ubuntu's partition, the part of grub that was installed to the MBR remains behind, and will cause you to be dropped to a grub recovery shell when you next try to boot. You can fix this by using a Windows recovery CD and "repairing" the MBR (by reinstalling the Windows bootloader).

---

### Post by JayKay3000 on 2010-06-11
I forgot that I always install ubuntu on a 2nd drive!

I guess this avoids problems like that.

---

