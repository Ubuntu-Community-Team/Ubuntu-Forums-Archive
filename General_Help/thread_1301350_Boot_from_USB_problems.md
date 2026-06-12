---
title: "Boot from USB problems"
date: 2009-10-25
forum: General Help
---

### Post by compy486 on 2009-10-25
I am currently running Ubtuntu 9.04 and wish to upgrade to 9.10. I downloaded the .iso image, and put it on a USB following the guide on the website. When I try to boot up from the USB, I get the following error:

Verifying DMI Pool Data...
Boot error

I have used a total of 3 USB's to boot from, and a number of different .iso files(ubuntu 9.10, windows xp) but any combination results in that error.

What I am trying to do is get the new version of ubuntu, then eventually with the knowledge of how to boot from USB, install windows 7 in a dual boot (but I dont want to worry about that yet. One problem at a time)

One more peice of info: this computer used to have Windows Vista on it, and I successfully instally ubuntu 9.04 (which I'm currently using) on it with the same USB I'm using now. I wiped out vista 100%.

---

### Post by compy486 on 2009-10-26
Update: 

On my laptop, which currently has Windows Vista on it, I successfully booted and logged into Ubtuntu 9.10! I can conclude the problem is with grub/ubuntu on my desktop, which is where I want to install it.

---

### Post by Mighty_Joe on 2009-10-26
> **compy486 said:**
> I downloaded the .iso image, and put it on a USB following the guide on the website. 

What website?  Exactly what did you do? 
I have had some success with [unetbootin]("http://unetbootin.sourceforge.net/") and more success with the [Live USB Creator]("http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator").  There's plenty that can go wrong, so you have to be really specific when telling us what you did.

---

### Post by compy486 on 2009-10-26
I downloaded the .iso image from the ubuntu main website ([http://www.ubuntu.com/getubuntu/releasenotes/910overview](http://www.ubuntu.com/getubuntu/releasenotes/910overview)) the first link under "download"

I burned the image to a USB using UNetBootin. I think the burn worked, because I was able to boot it up on a different computer (running vista), but this computer (running ubuntu 9.04) won't boot it. There must be a grub error, but thats just a guess.

Thanks for the response

---

### Post by jward3010 on 2009-10-26
USB Disk creator is undoubtedly the best I have ever used (In System > Administration menu). It's simple and it just works. 

I have never had a faulty or dodgy USB disk created, only incompatible laptops. But to get that ball rolling I had to burn an Ubuntu version that has it (9.04, 9.10) to disc, boot into Live version and use the program from there. Never a bad idea to have a disc copy of Ubuntu somewhere, USB's are not the most reliable devices and you could find it empty one day because it was too close to your mobile phone.

---

### Post by compy486 on 2009-10-26
Ok, I will try that program. I remember not using it before because when searching for the iso file, it only showed the file system folder; I didnt know how to navigate to the home folder.

On another thought: Is there a way to make grub recognize a bootable usb stick?

---

### Post by thejranjan on 2009-10-26
Its because you are using an Intel Desktop Board (seen this problem with intel 945GCP boards). All you have to do is to get into the BIOS setup and find something like "Mass storage emulation" it will be set to auto ...Change it to fixed disk...enjoy booting :KS Its not because of the .iso image nor the USB drives problem...The usb startup disk creator will do...

---

### Post by thejranjan on 2009-10-26
The mass storage emulation will be somewhere in the boot configuration.Hope you will find it out :KS

---

### Post by compy486 on 2009-10-26
Thank you very much for the help, I will try it out when I get home, and report how it goes

---

### Post by compy486 on 2009-10-26
I looked through the entire BIOS menu, but didn't find anything like what you were talking about. 

I looked up my motherboard, it is: **ECS MCP61PM-GM AM2 mATX Motherboard**. [http://support.gateway.com/s/MOTHERBD/Shared/4006254R/4006254Rsp2.shtml](http://support.gateway.com/s/MOTHERBD/Shared/4006254R/4006254Rsp2.shtml) 

Perhaps it has a differently named setting which essentially does the same thing?

---

### Post by t0p on 2009-10-26
Take a look at [this webpage]("http://www.duxcw.com/faq/computer/dmi.html").  It suggests (if you're sure the USB stick and its image are okay) that you may have a hardware problem.  Maybe the USB port you're using is faulty?

---

### Post by compy486 on 2009-10-26
Well, I dont know if the USB port is faulty because in ubuntu, it recognizes flash drives without error.

---

### Post by compy486 on 2009-10-26
Still no success... any other suggestions? I'm thinking its a grub problem or a BIOS setting (similar to what was mentioned, except for my motherboard)

---

### Post by mechro on 2009-10-26
I've just had a quick look at an M/board manual direct from ECS (as similar to your specs as I can find). Have you tried under **Advanced BIOS Features**?... either **Removable Device Priority** or **Hard Disk Boot Priority** might contain what you're looking for.

Of course, if Gateway have changed the basic ECS BIOS then the above might be irrelevant.

---

### Post by compy486 on 2009-10-26
Removable device priority just shows the name of the USB, so it detects it alright. Other then that, it doesnt do anything :(

---

### Post by mechro on 2009-10-26
> **compy486 said:**
> Removable device priority just shows the name of the USB, so it detects it alright. Other then that, it doesnt do anything :(

I don't know. I would guess if you had more than one removable device you could prioritise one of them. What can you set in Hard Disk Boot Priority?

---

### Post by compy486 on 2009-10-26
My main hard drive, and add-in cards

---

### Post by mechro on 2009-10-26
Try...

**Removable Device Priority** set as your "name of the USB"

**Hard Disk Boot Priority** set as "add-in"

Save and reboot.

If it doesn't boot your drive the first time, go into BIOS again and your drive might now be recognised.

---

### Post by compy486 on 2009-10-26
Alrighty, now my error message has a new line added to it:

"Verifying DMI Pool Data
AMD data change... Update New Data to DMI!
Boot error"

---

### Post by mechro on 2009-10-26
> **compy486 said:**
> Alrighty, now my error message has a new line added to it:

"Verifying DMI Pool Data
AMD data change... Update New Data to DMI!
Boot error"

Did you go back into the BIOS after this to check if there were any changes in the **Priority** settings?

---

### Post by compy486 on 2009-10-26
No changes that I see. Just simply lists the single usb under removable, and under hard drive it lists add-in cards, then the hard drive.

---

### Post by mechro on 2009-10-26
Hmmm, it's odd that the board seems to have all the options to boot from external drives but won't do it.

How about trying a different usb cable?

---

### Post by compy486 on 2009-10-26
What do you mean a different cable? If you mean different slot, I have tried a number of different ones.

On another note... is there a way to install the windows boot program (since the usb boot was successful on my vista laptop)

---

### Post by mechro on 2009-10-26
> **compy486 said:**
> What do you mean a different cable? If you mean different slot, I have tried a number of different ones.

On another note... is there a way to install the windows boot program (since the usb boot was successful on my vista laptop)

Different cable, different slot means pretty much the same thing, apart from the dangly bit of wire. ;)

I don't think the Windows boot program has much to do with Ubuntu booting from the USB. When you had a successful boot on the vista laptop wasn't the boot screen recognisable as Grub? If it was a Windows boot then I need to go and do some research on Ubuntu usb installations. :confused:

---

### Post by compy486 on 2009-10-26
Uhh... I have absolutely no clue. Also I'm out of ideas. 

Would it work if I try to burn the iso to a cd?

---

### Post by mechro on 2009-10-26
If the computer can boot from a CD then a LiveCD iso should work. I don't know whether the usb iso you've got is the same as a standard CD iso so you may need to download again.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by compy486 on 2009-10-26
Ok, ill give it a shot tommorow. Btw, thanks for all the help :)

---

### Post by mechro on 2009-10-26
> **compy486 said:**
> Ok, ill give it a shot tommorow. Btw, thanks for all the help :)

Cheers. I can go to bed now! :D

---

### Post by jward3010 on 2009-10-27
Also within the BIOS look out for options relating to booting off external devices or USB drive boot. They have to be set to enabled and thats it.

---

### Post by mechro on 2009-10-27
Done some further reading of the ECS manual...

In **Advanced Bios Features**, can you set **First Boot Device** to **Removable**?

---

### Post by compy486 on 2009-10-27
Good news! (stupid me) I realized you can upgrade to ubuntu 9.10 from 9.04 within the operating system, so I am now running 9.10! Afterwards, I burned an xp iso onto a CD, and holy hell it worked! I am now installing xp (soon to be upgraded to 7) alongside 9.10!

Thanks to all who have helped :D very much appreciated!

---

