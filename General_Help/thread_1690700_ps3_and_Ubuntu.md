---
title: "ps3 and Ubuntu"
date: 2011-02-18
forum: General Help
---

### Post by josephmills on 2011-02-18
Hello there I  am trying to put Ubuntu 9.10 on to a PS3 right now. Have been having some problems too say the least. I am a noob when it comes to computers, but there is only one way to get my feet wet. and that to jump in :)  these are the steps that I have taken so far. 

**Downloaded** 
         kboot and ubuntu 9.10 .iso and burned it to a disk
Source  ---------------  [www.psubuntu.com/wiki/UbuntuVersioins.com](www.psubuntu.com/wiki/UbuntuVersioins.com)
[B]
Set all the hardware on the ps3  the way it needs to be set up (I think )[/B]
         go to format hardrive >custom>partion10gig>quick format select yes or no. I select yes  
put the .iso cd burned cd in **PS3** 
restart **ps3**
        ** PS3  **setting>system settings>other os> select othors> start orthos =   yes no  I select yes  
 Shut down **PS3**
Restart ** PS3 **
then **kboot** starts  I press** enter** on the[B] wireless Keyboard
It starts to boot 
 [/B] [I]language>english 
place>united states 
keyboard config > no
then the of to look at the hardware.Reads all  
set up network I manually set up my wlan0
Name it Ubuntu>y/n    I select yes 
now it tries to set up the boot but half way though it I start getting errors 
file i///cdrom/pool/main/s/slang/libslang2_2.1.4-3_powerpc.deb is corrupt 
and I also get boot strap warring&#347; 
cant download libslang2
and this reads to a error in the boot set up it.  I can retry or go back I have tried retry and go back and every possible thing I could I tried re-burning the cd on slow and the same thing happens. :confused:
Do I need a new iso ? If so is there a good link for that :) bor is there something else that I am doing wrong thanks for taking the time to read this and look forward to the replies 

[/I]

---

### Post by williamts99 on 2011-02-18
> **josephmills said:**
> Hello there I  am trying to put Ubuntu 9.10 on to a PS3 right now. Have been having some problems too say the least. I am a noob when it comes to computers, but there is only one way to get my feet wet. and that to jump in :)  these are the steps that I have taken so far. 

**Downloaded** 
         kboot and ubuntu 9.10 .iso and burned it to a disk
Source  ---------------  [www.psubuntu.com/wiki/UbuntuVersioins.com](www.psubuntu.com/wiki/UbuntuVersioins.com)
[B]
Set all the hardware on the ps3  the way it needs to be set up (I think )[/B]
         go to format hardrive >custom>partion10gig>quick format select yes or no. I select yes  
put the .iso cd burned cd in **PS3** 
restart **ps3**
        ** PS3  **setting>system settings>other os> select othors> start orthos =   yes no  I select yes  
 Shut down **PS3**
Restart ** PS3 **
then **kboot** starts  I press** enter** on the[B] wireless Keyboard
It starts to boot 
 [/B] [I]language>english 
place>united states 
keyboard config > no
then the of to look at the hardware.Reads all  
set up network I manually set up my wlan0
Name it Ubuntu>y/n    I select yes 
now it tries to set up the boot but half way though it I start getting errors 
file i///cdrom/pool/main/s/slang/libslang2_2.1.4-3_powerpc.deb is corrupt 
and I also get boot strap warring&#347; 
cant download libslang2
and this reads to a error in the boot set up it.  I can retry or go back I have tried retry and go back and every possible thing I could I tried re-burning the cd on slow and the same thing happens. :confused:
Do I need a new iso ? If so is there a good link for that :) bor is there something else that I am doing wrong thanks for taking the time to read this and look forward to the replies 

[/I]

Sounds like a problem with the .iso image or the burn.  Check the md5sum hashes:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

