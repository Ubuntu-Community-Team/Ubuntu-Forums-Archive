---
title: "Running in to problems using Ubuntu on my netbook."
date: 2011-04-17
forum: General Help
---

### Post by ayupmiduck on 2011-04-17
Hi guys,

I would greatly appreciate some assistance.

I am currently duel booting Windows 7 starter and Ubuntu 10.10 desktop edition on my Samsung N145 netbook.

Unfortunately there are too many bugs for me to warrant using Ubuntu on my netbook, and I have not been able to find a way to fix them


[LIST]
[*]My issues are that I cannot adjust the brightness to an adequate level (screen seems very dull when compared to Windows)
[*]My function keys used for adjusting brightness do not work
[*]My netbook will not wake from suspend e.g.  when I close my netbook and re-open I get a blank screen.
[/LIST]

Ideally I would like to completely uninstall Ubuntu and rededicate my entire HDD to Windows 7 starter (currently each OS has approx half of my HDD each.)

I have not been able to find a guide which will show me how to do this without a Windows CD. Unfortunately Windows will not allow me to create a boot disk on to a USB pen drive and I do not have a CD drive as I am using a netbook. (You'd think Microsoft might have factored that in) 


So..... I figured, I could use Ubuntu as a back up to Windows on my netbook, so if somebody is unable to help with the above, could somebody please tell me if there is a way I can....


1. Re-partition my HDD to dedicate Ubuntu slightly over the minimum and give the rest to Windows

2. load Windows automatically on boot up (effectively hiding the grub menu)

Any assistance appreciated.

(Please note, I use Ubuntu exclusively on my desktop - So I do not require any comments on how "windows sucks")

I struggle with technical jargon so may I request that any instruction kindly offered is offered in its simplest form.


Many thanks
Kindest regards
Ayupmiduck

---

### Post by grahammechanical on 2011-04-17
I can only repeat some things that I have read in these forums. I do not speak from experience. I have read that:

1) it is best to use Windows to de-fragment the hard disk before re-partitioning.

2) it is best to use a Windows partition program to re-partition a Windows partition.

I am guessing that it will be possible to do the first but not the second. So, I ask, how did you install Ubuntu in the first place? Did you use a live USB stick to install? That will have a partitioner program on it. You could shrink the Ubuntu partition and increase the windows partition. Backup your data first.

As regards the menu, I suggest that in Ubuntu you install a utility called Grub Customizer (search the software centre for grub-customizer). This utility will let you easily set which OS to boot first and to reduce the menu display time to 1 second or even zero. But if Windows fails how do you get into your backup OS without the menu being displayed? Do you know how to do that?

Regards. I hope that this helps somewhat.

P.S. De-fragment? A process that copies the data that is scattered all over the hard disk into one continuous block. Linux file systems have a way of reducing hard disc fragmentation. So, it is not much of a problem. If a Windows partition is fragmented then the partitioner program may have to move data as well as resizing the partitions. Puts the data at risk

---

### Post by ububeginner on 2011-04-17
You can download the Windows 7 recovery cd [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

[Here]("http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/") is a guide on how to make a bootable windows installation usb.
I don't know, but I think it should work for the recovery cd as well

You will need a virtual drive to mount the ISO in Windows, I have used Virtual Clone drive in the past, it's free (as in free beer, not free speech) and it does the job

If you can boot from the usb you should be able to restore the windows bootloader

---

