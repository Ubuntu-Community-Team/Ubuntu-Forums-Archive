---
title: "Windows deleted GRUB. How to reinstall GRUB?"
date: 2010-12-29
forum: General Help
---

### Post by crixtiano on 2010-12-29
Hi,
I installed "Ubuntu Lucid" on a Dell notebook.

I partitioned the hard drive, Windows for half and half for Linux.

Yesterday, I accessed the notebook via the Windows partition and Windows 7 conducted a series of conferences on a screen similar to scandisk.

Now when I restart the computer, I can not login neither in Linux nor in Windows. 

The system can not find the HD or the partition or operating system.

I think Windows 7 removed Grub in the partition table.

Is there any way to restore Grub in my computer? Perhaps using a LIVE CD of Ubuntu?

Thank you!

Cristiano M. Magalhaes

---

### Post by akand074 on 2010-12-29
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by karthick87 on 2010-12-29
If you are not sure,then boot from a live cd and post the results of 
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) with code(#) tags..

---

### Post by wilee-nilee on 2010-12-29
> **karthick87 said:**
> if you are not sure,then boot from a live cd and post the results of 
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) with code(#) tags..

+1

---

### Post by Norcalli on 2010-12-29
Is it possible to share backups of our mbr? Because I was installing Windows 7 yesterday and I knew that it would overwrite the mbr, so I backed it up with
```
dd if=/dev/sdb of=./mbr.bin bs=446 count=1
```I don't believe there is anything unique about the mbr from a grub installed drive except maybe the 4-byte signature, so I think you could restore it from my backup using
```
dd if=./mbr.bin of=/dev/sdb bs=440 count=1
```
except that you should replace ***/dev/sdb*** with whatever drive you want and you should run this from a live cd. While people are generally afraid of 'dd', it isn't actually going to hurt to try to back up from my mbr because you can always just try some other method, so long as you remember to type "bs=440" and "count=1", otherwise **** will hit the fan.

---

### Post by wilee-nilee on 2010-12-29
> **Norcalli said:**
> Is it possible to share backups of our mbr? Because I was installing Windows 7 yesterday and I knew that it would overwrite the mbr, so I backed it up with
```
dd if=/dev/sdb of=./mbr.bin bs=446 count=1
```I don't believe there is anything unique about the mbr from a grub installed drive except maybe the 4-byte signature, so I think you could restore it from my backup using
```
dd if=./mbr.bin of=/dev/sdb bs=440 count=1
```
except that you should replace ***/dev/sdb*** with whatever drive you want and you should run this from a live cd. While people are generally afraid of 'dd', it isn't actually going to hurt to try to back up from my mbr because you can always just try some other method, so long as you remember to type "bs=440" and "count=1", otherwise **** will hit the fan.

Not needed.:)

---

