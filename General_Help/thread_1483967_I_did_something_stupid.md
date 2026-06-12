---
title: "I did something stupid"
date: 2010-05-15
forum: General Help
---

### Post by lostcarpark on 2010-05-15
During the upgrade to Ubuntu 10.04, a GRUB dialog asked me if I wanted to replace boot sectors. I think I accidentally overwrote the boot sector of the NTFS partition my Windows XP installation boots off.

I think I could fix it by booting off a Windows install disk and repairing the installation, but that would overwrite the GRUB MBR, so I'd have to repair that after.

Does anyone know of a Linux-based way to repair the Windows boot sector?

---

### Post by mcduck on 2010-05-15
> **lostcarpark said:**
> During the upgrade to Ubuntu 10.04, a GRUB dialog asked me if I wanted to replace boot sectors. I think I accidentally overwrote the boot sector of the NTFS partition my Windows XP installation boots off.

I think I could fix it by booting off a Windows install disk and repairing the installation, but that would overwrite the GRUB MBR, so I'd have to repair that after.

Does anyone know of a Linux-based way to repair the Windows boot sector?

That is a bit confusing.

You either have Grub on the MBR, or you have Window bootloader there. Not both.

So if you now installed Grub there, and use Windows to install it's bootloader to MBR instead, and then repair Grub again you end with the very same situation you started with, Grub on MBR... :D

Could you tell what is the exact problem you are having? If you are dualbooting Windows and Ubuntu you definitely want to have Grub on MBR, not the windows bootloader (otherwise your computer would just boot into Windows and you'd never get the chance to boot Ubuntu).

---

### Post by lostcarpark on 2010-05-15
Okay, thanks for the quick reply. Sorry if I was unclear, I'll try to explain better.

I definitely have GRUB on the MBR. When I boot, I get the GRUB menu, and I can boot into into Ubuntu without any trouble.

The problem is when I pick Windows XP, I get a black screen with a flashing cursor, and nothing else happens.

I can access the NTFS partition through Ubuntu without any problems.

This all leads me to suspect that I've corrupted the boot sector on the NTFS partition, and I have a feeling that I may gave overwritten it with GRUB during the upgrade. Is this possible?

---

### Post by inso_741 on 2010-05-15
run ```
sudo update-grub
``` and post the output here

---

### Post by miegiel on 2010-05-15
> **lostcarpark said:**
> Okay, thanks for the quick reply. Sorry if I was unclear, I'll try to explain better.

I definitely have GRUB on the MBR. When I boot, I get the GRUB menu, and I can boot into into Ubuntu without any trouble.

The problem is when I pick Windows XP, I get a black screen with a flashing cursor, and nothing else happens.

I can access the NTFS partition through Ubuntu without any problems.

This all leads me to suspect that I've corrupted the boot sector on the NTFS partition, and I have a feeling that I may gave overwritten it with GRUB during the upgrade. Is this possible?

Like **mcduck** said, you use one or the other. Grub replaces the windows bootloader and makes it't own entry for what partition to boot to when you want to boot windows. Grub(2) boots my windows fine. There might be something wrong with the UUID of the partition (grub uses the UUID to identify the correct partition).

A fast fix might be running :
```
sudo update-grub
```
in a terminal.

To check the UUID used to boot windows in take a look in */boot/grub/grub.cfg*, it should be below the *### BEGIN /etc/grub.d/30_os-prober ###* line (in mine the 1st entry below it).

To get the UUID of your windows partition, do :
```
sudo blkid -o value -s UUID /dev/sd**[COLOR="Red"]..[/COLOR]**
```
replace **[COLOR="Red"]..[/COLOR]** with your windows disk letter and partition number.

---

### Post by lostcarpark on 2010-05-15
Thanks for the information.

```
$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows NT/2000/XP (loader) on /dev/sda1
done
```

Got my UUID:

```
$ sudo blkid -o value -s UUID /dev/sda1
06802B15802B0AAF
```

This seems to check out with what's in /boot/grub/grub.cfg:

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
        insmod ntfs
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 06802b15802b0aaf
        drivemap -s (hd0) ${root}
        chainloader +1
}
```

This all seems consistent, which is why I suspect that the boot sector within the NTFS partition may be damaged.

---

### Post by john newbuntu on 2010-05-15
This solution has worked for a number of people who have installed grub on to the VBR/PBR of windows partitions.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by lostcarpark on 2010-05-15
> **john newbuntu said:**
> This solution has worked for a number of people who have installed grub on to the VBR/PBR of windows partitions.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Thanks for your help. I appreciate the support.

Testdisk did the job perfectly, and Windows now boots happily again.

---

### Post by john newbuntu on 2010-05-15
And thanks to our forum member meierfra for that post.

---

