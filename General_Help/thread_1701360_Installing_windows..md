---
title: "Installing windows."
date: 2011-03-06
forum: General Help
---

### Post by jordanC on 2011-03-06
Hi guys, after a long and painful process i finaly got my windows exe file to run! however, when i click install windows it comes up with "widnows cannot find a location to store any tempory files"
error code 0x80070490
can anyone help me out here? i want to completely remove ubuntu and install windows, cheers

---

### Post by elliotn on 2011-03-06
> **jordanC said:**
> Hi guys, after a long and painful process i finaly got my windows exe file to run! however, when i click install windows it comes up with "widnows cannot find a location to store any tempory files"
error code 0x80070490
can anyone help me out here? i want to completely remove ubuntu and install windows, cheers

u mean on wine?

---

### Post by jordanC on 2011-03-06
Yes im running the exe through wine

---

### Post by grahammechanical on 2011-03-06
So, you are trying to install Microsoft Windows through a program running inside a Ubuntu/Linux operating system with the purpose of removing Ubuntu. If you succeed you should be given a prize for doing the impossible.

The purpose of Wine is to let Linux users run Windows programs without needing to have Microsoft Windows Installed. It is not designed to run the Windows operating system itself.

If you want to run one operating system inside another operating system then you need to create what is called a virtual machine. It is a program that fools the second operating system into thinking that it is accessing the computer hardware when it is only accessing it through the host operating system.

If you want to install windows and remove Ubuntu at the same time, then just insert the Windows install disc into the CD drive and boot on the CD.

Windows will have difficulty installing onto a hard drive that has been formatted in a Linux format. It will have to format the disc to its own format. It will also need to store files temporarily on the hard disc as part of the install process. It cannot use the Linux formats. This could be why it is telling you it cannot find any temporary file space.

Regards.

---

### Post by jordanC on 2011-03-06
Okay well if thats impossible then im screwed.
ive tried making bootable discs but cant get them to work, when i re-boot my computer with the disc in, it just gets stuck on a black screen with a flashing blip i the top left, then starts ubuntu as normal. Before you ask, yes, my disc drive is top of the boot list in my bios, and ive tried to force boot from the disc.

---

### Post by veggen on 2011-03-06
You sir win the internet today.

---

### Post by gerowen on 2011-03-06
When running inside wine, the Windows disc will not have access to stuff it needs to actually remove Ubuntu.  Did you actually burn the ISO properly or just copy and paste it to the disc?  If when looking at the CD in a file browser you see the ISO file, it's wrong.  You have to burn it so that it extracts as it burns.  I've attached some screenshots to help you find the right options for burning an ISO in a manner that will make it bootable.

Just out of curiosity though, why in the world would you "want" to install Windows?  They charge you an arm and a leg, then put up false walls to limit what you can do with your computer unless you pay them even more money.  Let's not even start with the advantages of open source software.

---

### Post by jordanC on 2011-03-06
What? posting on here is usually pointless as you get people like you posting the most unhelpful comments you can get. So thanks for that

---

### Post by jordanC on 2011-03-06
My last comment was aimed at Veggan

---

### Post by jordanC on 2011-03-06
Thanks gerowen, ill try again and make sure i do it exactly how you show and let you know how i get on. I want to go back to windows because i havent really got to use ubuntu properly and found windows more user friendly, although i did really like some things about ubuntu.

---

### Post by gerowen on 2011-03-06
> **jordanC said:**
> Thanks gerowen, ill try again and make sure i do it exactly how you show and let you know how i get on. I want to go back to windows because i havent really got to use ubuntu properly and found windows more user friendly, although i did really like some things about ubuntu.

That's cool, as long as it works for you, go for it.  Ubuntu, or Linux for that matter, isn't for everybody, let me know how it goes, :-)

---

### Post by cchhrriiss121212 on 2011-03-06
Is this an official copy of Windows you are trying to install? Have you tried the boot disks on any other PCs?

---

### Post by jordanC on 2011-03-07
Blehhh still havent got it, can anyone help me out on teamviewer?

---

### Post by dtfinch on 2011-03-07
Which version of Windows? Installing is never easy on newer hardware. The XP installer doesn't support SATA without making a custom disk, for example, and I haven't seen a Vista install disk successfully boot on anything recent either.

---

### Post by Jerry N on 2011-03-07
> **dtfinch said:**
> Which version of Windows? Installing is never easy on newer hardware. The XP installer doesn't support SATA without making a custom disk, for example, and I haven't seen a Vista install disk successfully boot on anything recent either.

On my newest Gigabyte motherboard I had no problem installing and running XP without resorting to any custom SATA disks.  Win 7 is probably the easiest version of Windows to install yet, generally finding and installing necessary drivers without intervention. Win 7 seems to install in about the same time as Ubuntu 10.04.  

I would suggest that if the OP can't boot a genuine Windows install disk, he probably needs a new CD/DVD drive - those things fail rather regularly for me.  OTOH, if he is trying to install from a downloaded or pirate copy, then he should probably look elsewhere for help.

Jerry

---

### Post by jordanC on 2011-03-07
yeah im trying to use a downloaded version, but it worked on my mates computer so theres no reason why mine shouldnt. Only difference is he had xp, and ive got ubuntu.

---

### Post by jordanC on 2011-03-07
I have an exe for win7, which i cant get to work but i know it works on other computers,and an iso of xp, whici i also know works on other computers that are running windows. :/

---

### Post by FoxEWolf on 2011-03-07
Ummmm... You cannot install windows through Wine. How do you plan to remove ubuntu while you are using the install program within another program inside Ubuntu? This is like trying to pull a car through a keyhole. It cannot be done. If you want to remove ubuntu, obtain a boot cd of windows and then inside the install, wipe the partition and format NTFS.

---

### Post by cchhrriiss121212 on 2011-03-07
> Only difference is he had xp, and ive got ubuntu.
The real difference is that you have a different machine than he does, and if your PC will not boot a disk that works fine in other PCs you should get it checked by a professional. The OS you have installed will have no effect on your ability to boot from a CD, as that is handled by your BIOS and disk drive.

---

### Post by uRock on 2011-03-07
> **jordanC said:**
> yeah im trying to use a downloaded version,
We do not support piracy here on UF. Please seek help with this problem else ware.

Regards,
uRock

---

