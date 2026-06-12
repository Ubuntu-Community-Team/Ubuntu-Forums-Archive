---
title: "Can boot to Win7 after installing xbunit to a USB drive."
date: 2009-07-04
forum: General Help
---

### Post by Memnok on 2009-07-04
[FONT=Times New Roman][SIZE=3]EDIT: The title should be "Can _not_ boot to Win7 after installing xbuntu to a USB drive."  (I dont want xbuntu on the desktop, just the thumb drive).[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]I wanted to install xbuntu onto a thumb drive for use on my Eee PC. So in created a xbuntu disk and booted my desktop (not the Eee) from the disk. I chose to install xbuntu and selected the USB thumb drive for the installation.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]The install worked great, and I can boot my Eee into xbuntu from the USB thumb drive. But now my desktop dill not boot into Windows7.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I am receiving the following message: [/SIZE][/FONT]
 
> 
[SIZE=3][FONT=Times New Roman][FONT=Times New Roman][SIZE=3]GRUB loading stage 1.5.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]GRUB loading, please wait.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Error 21.[/SIZE][/FONT]
[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]I have tried to fix the problem by booting to the Windows7 install disk ant attempting an automatic boot repair. I have also dropped to the command prompt and done &#8220;bootsect /nt60 C:\&#8217;, &#8220;bootsect /nt60 ALL&#8221;, and &#8220;bootsect /nt60 SYS&#8221; and nothing has allowed the system to boot into Windows7.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I know, I know. I should have disconnected the cables to my drive&#8230; Bad me. Can someone point me in the correct direction on fixing my boot problem?[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]Thanks,[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Clint[/SIZE][/FONT]

---

### Post by michy99 on 2009-07-04
Can you boot to windows if the thumb drive is plugged in? If so, then the problem is that the grub file is on the thumb drive so that grub cannot find it if it is not plugged in.

---

### Post by Memnok on 2009-07-05
Thanks Michy, I do not know.  I will try that when I get home.
 
[COLOR=black][FONT=Verdana]Also, I think the thread title was a bit misleading.  It should have read "Can _not_ boot to Win7 after installing xbuntu to a USB drive".  Just for clarification, I don't want xbuntu on this particular desktop (it belongs to my daughter).  I only wanted a thumb drive that I could use to boot a netbook into xbuntu.  So I am trying to get Win7 back.[/FONT][/COLOR]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]

---

### Post by 3rdalbum on 2009-07-05
The way you tried to install to USB flash drive is incorrect - you should use the USB Startup Disk Creator program, or Unetbootin. Only use the ordinary install procedure when the target disk is always going to be in the computer that you are conducting the install on!

---

### Post by Memnok on 2009-07-05
> **3rdalbum said:**
> The way you tried to install to USB flash drive is incorrect - you should use the USB Startup Disk Creator program, or Unetbootin. Only use the ordinary install procedure when the target disk is always going to be in the computer that you are conducting the install on!

Any suggestions on how to fix Windows 7?

---

### Post by Memnok on 2009-07-05
> **michy99 said:**
> Can you boot to windows if the thumb drive is plugged in? If so, then the problem is that the grub file is on the thumb drive so that grub cannot find it if it is not plugged in.

I just checked, and with the USB drive in I still can not boot to Win7.

---

