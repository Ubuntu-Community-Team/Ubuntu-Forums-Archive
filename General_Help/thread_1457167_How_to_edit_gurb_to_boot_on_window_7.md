---
title: "How to edit gurb to boot on window 7 ?"
date: 2010-04-18
forum: General Help
---

### Post by ubfu on 2010-04-18
Having 2 hard disk ,  WD and SGate.Before I install ubuntu .I had install window 7 on Seagate hard disk. I took out the seagate hard disk and left WD on my pc.Installed ubuntu hardy on WD hard disk without a seagate since i have it as a backup external drive.
Now I plan to but back the seagate hard disk into the pc but when I boot , I didn't see any window 7 option.

How to boot back window 7 ? 
WD ( Window xp , Ubuntu hardy 8.04)
Seagate ( window 7 )

---

### Post by ubfu on 2010-04-18
Will it able to edit it ? or there's no way to do that ?

---

### Post by ubfu on 2010-04-18
What happen if there are multiple OS in multiple drive ? How do you guys set the booting ?

---

### Post by garvinrick4 on 2010-04-19
Here is some info:

[Grub 2 Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1195275")

Sorry this is not Legacy Grub it is Grub 2 not any good for 8.04.

---

### Post by john newbuntu on 2010-04-19
Go to your BIOS settings and change the boot order to boot from the other drive. Here's an example on how to change it:
[http://www.whitecanyon.com/how-to-change-boot-order.php](http://www.whitecanyon.com/how-to-change-boot-order.php)

---

### Post by djchandler on 2010-04-19
> **ubfu said:**
> What happen if there are multiple OS in multiple drive ? How do you guys set the booting ?

You could go into your BIOS and select the Windows drive to boot first. Using EasyBCD and the Windows boot loader, you can add the option to boot Ubuntu that way.

Your BIOS may have a boot menu you can use to select a boot drive too. It may not be necessary to alter GRUB or the Windows bootloader.

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

As usual, there's more than one solution to a problem. If you are more comfortable with Windows, EasyBCD may provide a simpler solution. Cnet staff editor's rating is 5 out of 5.

[http://download.cnet.com/EasyBCD/3000-2094_4-10556865.html](http://download.cnet.com/EasyBCD/3000-2094_4-10556865.html)

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by nerdtron on 2010-04-19
This is what I do with my two hard drives. connect both hard drives. be  sure the BIOS id set to boot from the ubuntu disk first. then boot into  Ubuntu, run the terminal and type:
```
sudo update-grub
```
enter your password and then it should detect your both OS.
This is GRUB2 though, not sure if it works for you.

---

