---
title: "Grub Error 22 and Unable to use Boot Cds?"
date: 2009-10-23
forum: General Help
---

### Post by Prioryjk on 2009-10-23
I was trying to uninstall Ubuntu and used a function on Gparter that deleted the partion I had set up for it, I restarted and the "Grub error 22" popped up.
Ubuntu was the only OP system I had installed on the harddrive but I was trying to boot up Win7, I tried both the win7 and origonal Ubuntu Boot disc to see if I could get it working but it still gave me the same message I then tried rearranging the boot order to boot the disc first and even removed the hardrive from the boot libary.
Nothing worked neither disc loads and I get stuck on a black screen, Any ideas?
I've heard that using a Super grub or Gparter boot disc might work so I'll be trying that once i've picked up some cds tomorrow but if the op system discs don't work I can't see how SG and GP will.
 
Any help appreciated :)

---

### Post by phillw on 2009-10-23
> **Prioryjk said:**
> I was trying to uninstall Ubuntu and used a function on Gparter that deleted the partion I had set up for it, I restarted and the "Grob error 22" popped up.
Ubuntu was the only OP system I had installed on the harddrive but I was trying to boot up Win7, I tried both the win7 and origonal Ubuntu Boot disc to see if I could get it working but it still gave me the same message I then tried rearranging the boot order to boot the disc first and even removed the hardrive from the boot libary.
Nothing worked neither disc loads and I get stuck on a black screen, Any ideas?
I've heard that using a Super grub or Gparter boot disc might work so I'll be trying that once i've picked up some cds tomorrow but if the op system discs don't work I can't see how SG and GP will.
 
Any help appreciated :)

Well, if you have removed the only OpSystem on your Hard-Drive, it is not going to boot off your hard-drive !!

I'm guessing you have your computer set to boot from HardDrive before the CD Drive.

This is a setting in BIOS. When you turn your computer on, it should display a message like press F2 for BIOS (Or, ESC, or F1... etc.).

You need to change your boot order to have the CD drive be the 1st boot device.

By the way - If you want to dual boot - i.e. have both ubuntu and windows on your system.. the answer to how to do that can be found here ....

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)


Phill.

---

### Post by Prioryjk on 2009-10-23
> **phillw said:**
> Well, if you have removed the only OpSystem on your Hard-Drive, it is not going to boot off your hard-drive !!
 
I'm guessing you have your computer set to boot from HardDrive before the CD Drive.
 
This is a setting in BIOS. When you turn your computer on, it should display a message like press F2 for BIOS (Or, ESC, or F1... etc.).
 
You need to change your boot order to have the CD drive be the 1st boot device.
 
Phill.
 
> I tried both the win7 and origonal Ubuntu Boot disc to see if I could get it working but it still gave me the same message I then tried rearranging the boot order to boot the disc first and even removed the hardrive from the boot libary.
Nothing worked neither disc loads and I get stuck on a black screen, Any ideas?
 
:confused:
 
I'll clarify as maybe its not understandable,
1. I deleted the Ubuntu partition (which took up all the hardrive)
2. Tried to boot with a Win7 disc which didn't work, so then I tried with the origonal Ubuntu disc to try and rectify to problem
3. Neither worked so I changed the boot order to boot from the cd first, didn't work so I tried different boot priorities using the Cd -rom drive removed the harddrive as a boot source etc 
4. None works 
 
Grub is still there and is trying to boot but I can't help it by inserting the disc or by deleting it to start over, thanks for the reply anyway :)

---

### Post by phillw on 2009-10-23
> **Prioryjk said:**
> :confused:
 
I'll clarify as maybe its not understandable,
1. I deleted the Ubuntu partition (which took up all the hardrive)
2. Tried to boot with a Win7 disc which didn't work, so then I tried with the origonal Ubuntu disc to try and rectify to problem
3. Neither worked so I changed the boot order to boot from the cd first, didn't work so I tried different boot priorities using the Cd -rom drive removed the harddrive as a boot source etc 
4. None works 
 
Grub is still there and is trying to boot but I can't help it by inserting the disc or by deleting it to start over, thanks for the reply anyway :)


Let me clarify.... GRUB is in your MBR (Master Boot Record) - As there is nothing for it to boot to, it will get very lonely / fed up / file for a divorce.

I repeat - It is the fact that your Hard-Drive is set to be the 1st boot device that is stopping your CD from being booted.

That is a BIOS setting and has nothing to do with your hard-drive.

You need to change your boot priority, in BIOS to put the CD drive **BEFORE** your hard-drive.

Hope that explains it better.

If you have physically disconnected your Hard-Drive, there is no way that grub could do anything !!!

2 things worth trying
1)  Clean your CD-Drive (the lens maybe mucky)
2) If you haven't already done so - disconnect your hard drive - it will either
a) boot off the CD (Which means your boot order in BIOS is wrong)
b) do nothing - in which case either the CD-Drive is
i) not in the boot order
ii) has a non-bootable CD in it
iii) is not talking to your computer (loose wire, jumper, generally broken)

I'll be around for a while, feel free to IM me on AIM.

Regards,


Phill.

---

### Post by Prioryjk on 2009-10-23
> **phillw said:**
> Let me clarify.... GRUB is in your MBR (Master Boot Record) - As there is nothing for it to boot to, it will get very lonely / fed up / file for a divorce.
 
Right gottcha loney computer = Divorce city
>  
I repeat - It is the fact that your Hard-Drive is set to be the 1st boot device that is stopping your CD from being booted.
 
That is a BIOS setting and has nothing to do with your hard-drive.
 
You need to change your boot priority, in BIOS to put the CD drive **BEFORE** your hard-drive.
 
Hope that explains it better. 
 
Okay I have been doing that seriously :)
> 
If you have physically disconnected your Hard-Drive, there is no way that grub could do anything !!!
 
2 things worth trying
1) Clean your CD-Drive (the lens maybe mucky)
2) If you haven't already done so - disconnect your hard drive - it will either
a) boot off the CD (Which means your boot order in BIOS is wrong)
b) do nothing - in which case either the CD-Drive is
i) not in the boot order
ii) has a non-bootable CD in it
iii) is not talking to your computer (loose wire, jumper, generally broken)
 
I'll be around for a while, feel free to IM me on AIM.
 
Regards,
 
 
Phill.
 Okay this sounds like plan, the cd drive seemed to be reading it but never seemed to recognise the disc, it was working yesterday but it seems the only logical solution atm

---

### Post by Prioryjk on 2009-10-23
Right its all up and running, turns out my Disk drive decided to stop working the day I wanted to install a new OP, swaped it with another I had lying about and it recognised the disk np, thanks for the help phillw and sorry for being a pain :)

---

### Post by phillw on 2009-10-23
> **Prioryjk said:**
> Right its all up and running, turns out my Disk drive decided to stop working the day I wanted to install a new OP, swaped it with another I had lying about and it recognised the disk np, thanks for the help phillw and sorry for being a pain :)

Motto of the story: Trust no-one & nothing :)

Been there, got the 'T'-Shirt and the bumps on my head from bashing it against the wall - lol

:popcorn:

And, btw - it's no problem - glad to have been of help - Dual Boot *DOES* have it's advantages !!

Phill.

---

