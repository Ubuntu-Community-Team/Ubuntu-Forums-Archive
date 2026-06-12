---
title: "The Screen Is Black after Boot load"
date: 2010-11-03
forum: General Help
---

### Post by Phareouh on 2010-11-03
Hi there , after i installed using Wubi the 64 version, on my Win 7 , 

when i get the boot loader screen i choose Ubuntu , and then i get to choose recovery mode or Normal mode , in either , i get some sort of a list , and then i Get a Black Screen , Nth ,

But i hear a sound of May be Ubuntu starting ...:confused::confused:

so what can i do to see my Ubuntu ????

is there is away for help , i just need to run Both my Original Reinstalled Win 7 64 bit ,
and my Ubuntu.. So i used Wubi as an easy answer :)


so Can any help 

thankx

---

### Post by dyathinkesaurus on 2010-11-03
Is this the latest version of Uunto (10.10)?

What graphics card do you have installed?

---

### Post by drs305 on 2010-11-03
It could be a video problem. When you get to Ubuntu's grub menu within Windows, try pressing "e" to edit the menu entry. Then cursor to the end of the "linux" line, which probably ends with **quiet splash**. Add **nomodeset** to the end of the line and then press CTRL-x to boot. 

If it now boots normally, you will need to add your video driver - probably via the System, Administration, Additional Drivers/Hardware Drivers.

---

