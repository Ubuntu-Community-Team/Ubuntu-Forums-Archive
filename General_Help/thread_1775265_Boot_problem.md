---
title: "Boot problem"
date: 2011-06-04
forum: General Help
---

### Post by kashiqirphan on 2011-06-04
I installed Ubuntu on a flash drive and it was successful but the problem is am not able to boot windows 7 on my computer with out inserting the flash drive. As I am new to Linux based OS I have no idea what to do, pls help me out.

Thanks in Advance !

---

### Post by jamesisin on 2011-06-04
It sounds like you also installed the boot-loader on the flash drive.  Without a functioning boot-loader the machine doesn't understand where to look for an operating system.

---

### Post by kashiqirphan on 2011-06-04
Thanks jamesisin. But how can i fix it ?????

---

### Post by YesWeCan on 2011-06-04
It may be the opposite. When you install Ubuntu the installer seems to default to putting the linux Grub master boot record (MBR) on the fist hard disk, which would be your Windows disk, but the rest of Grub's files are on your flash drive. So Grub won't work without the flash and Windows won't boot because its MBR has been over-written.

This is the dumbest default behaviour of Ubuntu's installer but I musn't keep ranting about it. ;)

So you need to reinstall the Windows MBR. You can do this using your Windows CD and run 'fix mbr'.

You can also do this from Ubuntu live CD:
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

(assuming sda is you Windows drive - which is almost certainly is. You can check in System/Admin/Disk Utility)
You should now be able to boot Windows.

But you won't be able to boot Ubuntu. You need to install Grub to the flash drive and not to the Windows drive.

---

### Post by jamesisin on 2011-06-04
After following YesWeCan's instructions you could also just use the Windows boot-loader to run Ubu, which shouldn't be any more complicated.

---

### Post by Hedgehog1 on 2011-06-04
We can give you the commands to set the boot loader and the grub menu to use your hard disk instead of the flash drive, but we need to know your disk & partition layout.

Please do this from Ubuntu:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge***

:KS

---

