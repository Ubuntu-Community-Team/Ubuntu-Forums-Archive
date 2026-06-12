---
title: "Stupid Windows Won't Boot"
date: 2009-12-26
forum: General Help
---

### Post by LucidStrike on 2009-12-26
After I installed Kubuntu 9.10, I couldn't log into Windows XP. It shows in GRUB and starts to boot, but, even when attempting 'Safe Mode', it stops at gagp30kx.sys and reboots. XP was on the computer first, OEM I think. In Ubuntu, I couldn't mount the Windows partition. I've ignored the Windows partition since, but need to use some programs I'd installed on it.

I installed testdisk and it could see and move files. I have successfully moved some documents from the Windows partition to the Ubuntu partition. Like I said though, I need to run some Windows programs now. I had testdisk analyse the drive and got this:

```
Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: Incorrect number of heads/cylinder 240 (FAT) != 255 (HD)
 1 P FAT32 LBA                0   1  1  1240 119 63   19928097 [HP_RECOVERY]
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 2 * HPFS - NTFS           1240 120  1 13398  28 26  195312500 [HP_PAVILION]
 3 E extended             13399   0  1 30400 254 63  273137130
 5 L Linux                13399   1  1 30030 254 63  267193017
   X extended             30031   0  1 30400 254 63    5944050
 6 L Linux Swap           30031   1  1 30400 254 63    5943987
```

I'm guessing the problem has to do with those warnings, as I see the first partition ends where the Windows partition begins.

I apologise, if this seems nonsensical. I'm struggling against sleep and desperate.

---

### Post by lidex on 2009-12-26
Did you resize (shrink) the windows partition before installing Karmic?

---

### Post by LucidStrike on 2009-12-26
Sorry about the delay. Yes, I did. I think I did it from Ubuntu live.

---

### Post by QwUo173Hy on 2009-12-26
Just a suggestion, but when I had trouble with my windows installation (also after an Ubuntu install), it was the general computing websites that helped me most, because they had more information on the windows errors.

I hope you get it sorted though. It's not nice when this happens and it seems that we just can't promise a safe dual-boot experience - at least for the windows user.

---

### Post by Leppie on 2009-12-26
try looking for hiren's boot cd, it contains several good partition managers. you maybe able to fix these errors with one of them.

---

