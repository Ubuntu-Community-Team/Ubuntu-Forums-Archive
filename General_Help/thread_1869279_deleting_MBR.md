---
title: "deleting MBR"
date: 2011-10-25
forum: General Help
---

### Post by Lakeside5 on 2011-10-25
I have a problem, I have a big server (has RAID and 4 hard-drives, all dual core). I tried to have Ubuntu Linux installed but it seems this strange server does not LIKE Linux, so I tried to remove it, and try out the Window's Server Trial, for now.  Seems I cannot do that either because part of the linux is still there, and trys to boot up but it is an error. My friend says this means the Master Boot Record is still on there and needs to be removed, so he have me a tools disc, with many programs on it. I set the BIOS to boot from the CD, but have no clue WHICH of these programs will do the job. Does anyone know how to get rid of this stupid MBR?  Thanks!

---

### Post by Lakeside5 on 2011-10-25
I can list the programs on the CD if you like (I assume it is one listed in the 'hard drive' category, there are 3 categories.).  Or you can suggest some other free online tool to remove it, thanks again :)

---

### Post by garvinrick4 on 2011-10-25
It is not what you are removing but what are you going to put in. It will overwrite
existing in mbr. So get disk you would like to install its grub into mbr and just install that.

---

### Post by Lakeside5 on 2011-10-25
Sorryn not too good at this, not too sure I understood. I got a trial version of the Windows Server 2008, (would RATHER use Linux, but the server will NOT play nice with linux) and put it on a usb stick, set the BIOS to boot from the usb, and thought I had installed windows server ok (it went through ALL the steps and it looked good) BUT, upon reboot, that pesky purple ubuntu screen popped up, then the error page (some code in terminal, with curser prompt). So trying to overewrite it with another program didn't work, if that's what you meant. Thanks though :)

---

### Post by satanselbow on 2011-10-25
> **Lakeside5 said:**
>  (some code in terminal, with curser prompt). 

Might be handy to know exactly what that same text was... did it mention "grub" or "grub rescue"?

Anyway - this page is a howto on how to fix the windows server 2008 mbr / boot. You will have to adjust paths to suit your purpose and start by, again, booting from your USB and entering the recovery console ;)

[http://ezinearticles.com/?How-to-Fix-Windows-Server-2008-Boot-Loader&id=1590479](http://ezinearticles.com/?How-to-Fix-Windows-Server-2008-Boot-Loader&id=1590479)

---

### Post by garvinrick4 on 2011-10-25
Whichever you boot from HDD or USB flash drive or USB drive you boot from what is in
its mbr. The first few sectors of that drive will have a small program (grub we will call it)
that points it towards the boot files from operating system intended to boot. 
So if you have a Windows server on a flash drive if you boot from it will not have Linux grub2 in its mbr unless you installed it there. Where is your Windows server 2008 installed?
Do you have disks, will use BCD as a grub, easy to install. Just need to know where you
need to install what? Can use Lilo from Ubuntu disks if have to? So there is a salution I believe.

##Looks like a good link in post #5

---

