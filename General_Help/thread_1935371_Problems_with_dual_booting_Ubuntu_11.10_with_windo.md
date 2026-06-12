---
title: "Problems with dual booting Ubuntu 11.10 with windows 7"
date: 2012-03-04
forum: General Help
---

### Post by Jakob45 on 2012-03-04
I have recently installed Ubuntu 11.10 on my PC which is running Windows 7. I downloaded the iso and burnt it to disk then booted Ubuntu off the disk and selected the "install along side current operating system" option. After the installation I was unable to boot either Windows 7 or ubuntu. I have managed to restore the windows boot with the "bootrec.exe /FixMbr" command off a restore disk but I am still unable to boot ubuntu. I have tried ubuntu boot repair off the install CD but this just took me back to square 1 (no OSs at all)
Any help would be great cheers

---

### Post by Mark Phelps on 2012-03-04
First thing you probably need to do (again) is get Win7 booting.  If what you did fixed it last time, then do the same thing again.

Once you have Win7 booting OK, then read through the details in the link below about reinstalling GRUB after Windows is working:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by lindsay7 on 2012-03-04
This may help.

[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

---

### Post by sachithD on 2012-03-04
I'd rather do like this, it's less messy
First install/recover Windows 7
then,
if you don't have important stuff in your ubuntu partition(s) just install it again and you should be fine,
  if you are installing a new copy make sure you give out partitions to your /home, /boot   and / obviously

Because when trying to restore the bootloader (GRUB) can be messy when untrusted ways are used specially inside windows, and if you don't know grub commands you can be in real trouble (for some time)

So try avoiding it by reinstalling Ubuntu 
Hope this helps

---

### Post by oldfred on 2012-03-04
One of the easier ways to fix things is Boot-Repair. You can download it into the Ubuntu liveCD or download it as a repairCD on its own.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by Jakob45 on 2012-03-05
Ok I have reinstalled Ubuntu and had the same problem after the hardware check screen on startup nothing but black with flashing cursor with no key strokes effective. I repaired windows then ran a boot info off boot repair here is the URL
[http://paste.ubuntu.com/870397/](http://paste.ubuntu.com/870397/)
Would be grateful if anyone could take a look

---

### Post by oldfred on 2012-03-05
Were you not able to boot Windows from the grub menu? Or did you not get grub menu? Boot script looks normal to me.

Often if you get menu, but then get black screen or it only shows a cursor it is a video issue. What video card/chip do you have.

You can reinstall grub2 to the MBR. Then on grub menu use e to edit Ubuntu entry and add nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by Jakob45 on 2012-03-05
On startup I don't even get as far as the grub menu. I'm running a nVidea GeForce G 105 M. Is it possible to get the grub menu if when booting live CD you bring up the advanced options menu as described here
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
(I know i'm not expert but the boot script seems to start going wrong round line 307 of the file, although this may be because bootrec.exe /FixMbr wiped grub out)

---

### Post by oldfred on 2012-03-05
You have to be booting from grub in the MBR.

You can hold shift key from BIOS until menu appears, if it is not shown automatically. But with two systems it should come up on its own.

---

### Post by Jakob45 on 2012-03-06
Ok I held shift on startup as you suggested but got a message saying GRUB loading but then nothing happened after that.
Here is the boot info with grub installed maybe it will help
 
[http://paste.ubuntu.com/871840/](http://paste.ubuntu.com/871840/)

Thanks

---

