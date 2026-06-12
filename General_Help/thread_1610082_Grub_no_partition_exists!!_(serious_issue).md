---
title: "Grub no partition exists!! (serious issue)"
date: 2010-10-31
forum: General Help
---

### Post by DeeJayCruiser on 2010-10-31
hey all i have read through the countless grub posts but here is my issue and i can't seem to find one taht addresses it exactly.

I had dual boot win 7 and ubuntu, ubuntu was taking too much space so i went to system manager in windows and virtual drive manager and erased the partition with ubuntu.

Restarted my computer and had the grub error come up and i can't get around it. what do i do?

---

### Post by DeeJayCruiser on 2010-10-31
bump

---

### Post by coffeecat on 2010-10-31
> **DeeJayCruiser said:**
> i went to system manager in windows and virtual drive manager and erased the partition with ubuntu.

Oh dear. When you erased the Ubuntu partition you erased grub stage 2 and the grub configuration files, so now grub stage 1 on the mbr has nowhere to go. Hence the error message.

What to do now depends on what you want to do. Do you want just Windows back, or do you want a Windows/Ubuntu dual-boot?

If you want a Windows/Ubuntu dual-boot, simply reinstall Ubuntu into the free space you've created on the hard drive and the installer will set up grub again with a dual-boot menu so that you can boot both Windows and Ubuntu.

If, however you want Windows only on that machine, you simply have to repair the Windows mbr, and there are three simple ways.

1 - With the Microsoft Windows 7 install disc. It has to be a Microsoft disc, not an OEM restore disc. If you don't have one, then....

2 - With the Windows 7 repair disc you created with the utility in Windows 7. You did create one, didn't you? Ah well, in that case you'll have to...

3 - Use the Ubuntu live CD. Somewhat counter-intuitively you can install lilo in the live session and use that to restore the Windows mbr. If you need to do that, post back and I'll explain the straightforward procedure.

---

### Post by _Fordy on 2010-11-01
> **coffeecat said:**
> 

3 - Use the Ubuntu live CD. Somewhat counter-intuitively you can install lilo in the live session and use that to restore the Windows mbr. If you need to do that, post back and I'll explain the straightforward procedure.

Sadly, I am in exactly the same situation.

If you could go into 3 in more detail, that'd be fab. Win7 startup repair "didn't find any errors" -_-

---

### Post by coffeecat on 2010-11-01
> **_Fordy said:**
> Sadly, I am in exactly the same situation.

If you could go into 3 in more detail, that'd be fab. Win7 startup repair "didn't find any errors" -_-

With the Win 7 disc you may have to drop to the command prompt. From Microsoft:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

But if you want to use the Ubuntu live CD....

Boot into the live session and ensure you are connected to the internet. Then, from a terminal:

```
sudo apt-get install lilo
sudo sudo lilo -M  /dev/sda mbr
```

If you get an error after the first command, do this command first and try again.

```
sudo apt-get update
```

---

