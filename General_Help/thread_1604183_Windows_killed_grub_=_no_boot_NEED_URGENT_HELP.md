---
title: "Windows killed grub = no boot NEED URGENT HELP"
date: 2010-10-23
forum: General Help
---

### Post by crazymao on 2010-10-23
so i installed ubuntu 10.04 on my laptop with windows 7 preinstalled. it worked fine but after a reboot from windows 7 i get a "no module found" error. when i try to but into my usb with ubuntu installed on it it gives me a "ntldr not found" error. i researched both errors but found no workable solutions. so i cant boot into any partitions on my hard drive plus i cant use any external hardware to fix the problem :mad::mad::mad::mad::mad::mad::mad: please help as it is my main computer and i really need it. thank you

---

### Post by xircon on 2010-10-23
Is this a Dell?  If it is boot off a live CD and reinstall grub, then boot windows and remove Dell Datasafe, reboot and reinstall grub (again I know).

I am trying to find the grub instructions, back in a bit.

edit - [http://ubuntuforums.org/showthread.php?t=1581099&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=1581099&highlight=reinstall+grub)

---

### Post by sikander3786 on 2010-10-23
Windows and Ubuntu is installed on the same HDD alongside each other?

> usb with ubuntu installed on it it gives me a "ntldr not found" error

Did you change the boot order to boot from USB instead of HDD?

It would be better if you manage to boot off a Live CD or USB and post the output of bootinfoscript so we exactly know what you've got and help accordingly. Instructions and script here,

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Please wrap the output with proper code tags #.

---

### Post by crazymao on 2010-10-23
> **sikander3786 said:**
> Windows and Ubuntu is installed on the same HDD alongside each other?

yes they are

> **sikander3786 said:**
> Did you change the boot order to boot from USB instead of HDD?

no but i go into boot selection at the start and then select usb

> **sikander3786 said:**
> It would be better if you manage to boot off a Live CD or USB and post the output of bootinfoscript so we exactly know what you've got and help accordingly. Instructions and script here,

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

the problem is that when i try to boot into my usb it gives me the ndrtl error and my live cd doesnt do anything after the main menu which is weird because it worked before. if i could boot into a live cd i would copy all my windows data and reinstall ubuntu on the entire hardrive which i believe would fix the problem. i will attempt to make another live cd and see if that works but any alternative solutions are welcome

ps: thanks for all the help
pss: i read something about super grub boot or something like that, could i use that to fix my problem, if so how?

---

### Post by sikander3786 on 2010-10-24
> no but i go into boot selection at the start and then select usb

ntldr missing is a Windows error meaning that the computer is booting from HDD, not from the USB. How was the Live USB created? I doubt if it is bootable. Try with unetbootin.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Once you are able to boot off a Live USB, bootinfoscript will help us in helping you. You also need a Live USB or Live CD to reinstall Grub.

Super Grub is another option but someone else will have to jump in for the Super Grub instructions. I didn't ever need it.

---

