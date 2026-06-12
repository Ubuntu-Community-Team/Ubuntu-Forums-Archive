---
title: "Ubuntu Help please"
date: 2010-01-27
forum: General Help
---

### Post by turc0033 on 2010-01-27
The OS Ubuntu is required for one of my CE courses. I have a laptop and a desktop, both have windows 7. I didn't want to completely install Ubuntu and delete Windows 7, so i downloaded Ubuntu and saved it on a compact disc. I then restarted my computer and went into the Boot Menu and ran Ubuntu through my RAM (so it didnt replace Windows 7).

Once Ubuntu was installed and operating, i inserted my flash drive and installed Ubuntu into my flash drive - making my flash drive a hard drive. I then restarted my computer and it gave me the option to either boot in windows 7 or Ubuntu.

Here's the issue, it will only load windows 7 if, and only if the flash drive is plugged in. If the flash drive isnt plugged in, this will happen:

initial loading screen, then a black screen with the message: 
Grub loading
error : no such disk
grub rescue> _

Any suggestion on how to fix this issue?

---

### Post by t4thfavor on 2010-01-27
You need to install grub on the HDD in your pc. I would recommend you repartition your HDD leaving space for an ubuntu install (10gb is plenty) then reinstall ubuntu onto that. The USB one will not work correctly in your situation. And it's slow anyways.

---

### Post by puneeth@web on 2010-01-27
You hav installed the ubuntu in the Pendrive with no problem
 
But while installing the ubuntu
 
you should config your GRUB loader so as to show Windows 7 and select its boot partion
since you dint .it wont recognize winndows 7 and search for the Pendrive's contents...
since you want to restore windows i recommend the repair option provided in the windows 7 disc 
 
if this doesnt work then 
insert the boot up disk(Used for back up's)of windows  and your windows will boot normally
now run MSCONFIG and replace the grub loader with default loader...
 
if this doesnt work 
i really dont hav ne soln.
 
see since you want to work on ubuntu why dont you try ubunty netbook os it installs into your pendrive .....
if you insert the pendrive during the boot up the pendrive boots and if you want to use windows 7 just shutdown and remove pendrive and boot again....
 
here is the link
 
[http://www.ubuntu.com/GetUbuntu/download-netbook](http://www.ubuntu.com/GetUbuntu/download-netbook)
 
if you want a better solution since you want to install ubuntu
 try using Virtual box given by sun
u can install ubuntu inside windows and just run it like another program...
 
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by hhlp on 2010-01-27
it seem you install bot in your flash or pen drive.....

see how to recover grub, Reinstalling GRUB 2 from the LiveCD

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by puneeth@web on 2010-01-27
**Re: Ubuntu Help please** 
You hav installed the ubuntu in the Pendrive with no problem

But while installing the ubuntu

you should config your GRUB loader so as to show Windows 7 and select its boot partion
since you dint .it wont recognize winndows 7 and search for the Pendrive's contents...
since you want to restore windows i recommend the repair option provided in the windows 7 disc 

if this doesnt work then 
insert the boot up disk(Used for back up's)of windows and your windows will boot normally
now run MSCONFIG and replace the grub loader with default loader...

if this doesnt work 
i really dont hav ne soln.

see since you want to work on ubuntu why dont you try ubunty netbook os it installs into your pendrive .....
if you insert the pendrive during the boot up the pendrive boots and if you want to use windows 7 just shutdown and remove pendrive and boot again....

here is the link

[[COLOR=#444444]http://www.ubuntu.com/GetUbuntu/download-netbook[/COLOR]]("http://www.ubuntu.com/GetUbuntu/download-netbook")

if you want a better solution since you want to install ubuntu
try using Virtual box given by sun
u can install ubuntu inside windows and just run it like another program...

[[COLOR=#444444]http://www.virtualbox.org/wiki/Downloads[/COLOR]]("http://www.virtualbox.org/wiki/Downloads")

---

### Post by efflandt on 2010-01-27
You made a common mistake because Ubuntu installation does not tell you where is is going to put the initial grub boot loader, unless you use the **Advanced** button at the summary screen just before that actual installation proceeds.  So you accidentally put grub in your main hard drive mbr instead of the mbr of the USB flash/drive.

If you want to put Ubuntu on the hard drive per **t4thfavor**, first use administration tools in Win7 itself to shrink its partition by 10 GB (or however much space you want to use).  Then during Ubuntu installation it is best to configure Linux partition(s) exactly how you want them instead of letting it possibly automatically resize things.

If you want to restore Win7 to boot from its hard drive without grub, boot the Win7 system or recovery disk, and there is a menu selection on that to restore boot (which should put the Windows mbr back on your internal drive).

Since you currently do not have grub on your USB flash, in order to have that boot on any computer, you will need to install grub2 on the flash drive that per the link from **hhlp**.

---

### Post by CNBarnes on 2010-01-27
Well... this answer may be a little late for you, but I'll throw it out there for you anyway.

Rather than partitioning your hard drive, I would STRONGLY suggest running either virtualbox or VMWare Workstation (which could be free since you're doing this for a class) and running your Ubuntu in a virtual machine.

Doing this has many great advantages:

(1) no messing with grub
(2) you can use both Windows and Ubuntu on the same machine at the same time
(3) if you mess up, you can just erase the virtual machine and start over w/o toasting your baseline OS



PS: I haven't dual-booted a computer in 4 years.  I ALWAYS do them using VMware....

---

