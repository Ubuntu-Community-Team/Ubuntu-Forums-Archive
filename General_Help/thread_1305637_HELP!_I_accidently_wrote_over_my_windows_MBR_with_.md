---
title: "HELP! I accidently wrote over my windows MBR with grub! Cannot add it to grub either!"
date: 2009-10-30
forum: General Help
---

### Post by OmegaAI on 2009-10-30
I cannot repair windows bootloader and I cannot add windows to my grub because I keep on getting this error:
```
omega@omega-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-14-generic-pae
&#8220;Adding Windows&#8221;
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/mapper/isw_ecigiedefb_Alpha1
grub-probe: error: no mapping exists for `isw_ecigiedefb_Alpha1'
done

```My windows is on a RAID0 and I didn't know that 9.10 supported RAID when I did this (use to just not even work if I accidently used /dev/sda)


How would I go about putting my windows MBR back?

I an reinstall it (my RAID can be accessed through ubuntu :D). I just got to backup my windows stuff.

---

### Post by sliketymo on 2009-10-30
Do you have your windows installation disk?

---

### Post by panicy on 2009-10-30
He is right.  You'll need your windows disk and boot into recovery console.  Run the command "fixmbr" and "fixboot", without the quotes of course.  That'll rewrite the windows bootloader to the MBR.  If you can't find you windows disk and you have a i386 folder then you can run the command "x:\i386\winnt32.exe /cmdcons" (or sometimes x:\windows\i386...")where x is the drive that the i386 resides in

---

### Post by OmegaAI on 2009-10-30
> **sliketymo said:**
> Do you have your windows installation disk?
Yep
> **panicy said:**
> He is right.  You'll need your windows disk and boot into recovery console.  Run the command "fixmbr" and "fixboot", without the quotes of course.  That'll rewrite the windows bootloader to the MBR.  If you can't find you windows disk and you have a i386 folder then you can run the command "x:\i386\winnt32.exe /cmdcons" (or sometimes x:\windows\i386...")where x is the drive that the i386 resides in
I fixed it using this method

Thanks guys

---

### Post by coolgenes on 2009-10-30
Try Sun VirtualBox I think it is even better than dual booting because you can switch between OS with a mouse click.  Just need to have enough RAM

---

