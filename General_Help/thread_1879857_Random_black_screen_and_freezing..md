---
title: "Random black screen and freezing."
date: 2011-11-12
forum: General Help
---

### Post by Emera on 2011-11-12
Sometimes when I am doing things on my laptop, I get completely frozen and have to restart or a random blank screen pops up and I can't do anything and have to restart. I don't know why it keeps doing this. I had to reinstall ubuntu 10.04 but it is STILL doing it. My ubuntu version is 10.04 and I really want to get this fixed. Any help would be greatly appreciated. Thanks.

---

### Post by Rubi1200 on 2011-11-12
Hi and welcome to the forums :)

Please post the make/model of computer and full specifications, especially RAM and graphics card.

---

### Post by iondoarion on 2011-12-02
> **Rubi1200 said:**
> Hi and welcome to the forums :)

Please post the make/model of computer and full specifications, especially RAM and graphics card.

Hi,


TY! I am also new to the forums. :) Hope that in a few months I can also contribute.


I have the same problem but only when I am not at the PC (idle). After I get the black screen and I have to reboot. I am using Ubuntu 11.04 (64bit)

Here are the full specifications (I think that you should know about):
[B]
ASUS K72JT-TY165D[/B]
-----------------------------------------
 [Intel]("http://www.evomag.ro/vizualizare_cuvant.php?idcuvant=41")® Core™ i5 Mobile 
 i5-480M
2660 Mhz
3072 Level 2 
 2400  (FSB)
-----------------------------------------
RAM  4096 MB 
 2x2048 
DDR3 1066MHz/PC3-8500 
-----------------------------------------
500 GB 
SATA
5400 RPM
-----------------------------------------
AMD Radeon HD 6370M
1024 
-----------------------------------------




Thank you!:)

---

### Post by Huss on 2012-01-05
I have a similar issue on my HP tx2. The screen goes blank while in use after approximately 10-20 minutes. Ctrl-alt-del or ctrl-alt-f1 do nothing. I've found I need to leave it off for a while before I can reboot properly - prob for 5 mins

64-bit (AMD Turion X2 Ultra Dual-Core Mobile Processor ZM-86 (2.4 GHz)), ATI Radeon HD 3200 Graphics, 4gb ram.

My only thought is that the laptop gets quite hot which might trigger the problem. Not sure though, the previous owner had Windows on it and no problem.

Any trouble shooting advice?

---

### Post by imachavel on 2012-01-06
screen goes black. wow could be memory, could be driver. sounds like windows. in hibernate? also sounds like windows. I have no idea but I'll give it a crack. When you boot up, select f8 I believe, hold it down hard, don't just tap it. If it gives you an option screen, you might see 'memory test.' select this, it will test all sectors on the processor and ram, and will take quite a few hours.

try to hit ctrl+alt+delete. see if gets you to the restart screen or reboots the machine. Any usb devices installed that you can remove and plug back in after boot?(only key board and mouse if not ps/2 will give problems if not read by bios at boot) If so remove them. 

I found this old fix for this same bug:

[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

I haven't tried it, so I'm not going to say I recommend it

---

### Post by 2F4U on 2012-01-06
> **Huss said:**
> I have a similar issue on my HP tx2. The screen goes blank while in use after approximately 10-20 minutes. Ctrl-alt-del or ctrl-alt-f1 do nothing. I've found I need to leave it off for a while before I can reboot properly - prob for 5 mins

64-bit (AMD Turion X2 Ultra Dual-Core Mobile Processor ZM-86 (2.4 GHz)), ATI Radeon HD 3200 Graphics, 4gb ram.

My only thought is that the laptop gets quite hot which might trigger the problem. Not sure though, the previous owner had Windows on it and no problem.

Any trouble shooting advice?

Is suspend/hibernate working on this machine? If yes, try to close and re-open the lid after the screen went black.

With respect to overheating, what graphics driver are you using? Did you open the case and clean the inside from dust?

---

### Post by 2F4U on 2012-01-06
> **iondoarion said:**
> Hi,


TY! I am also new to the forums. :) Hope that in a few months I can also contribute.


I have the same problem but only when I am not at the PC (idle). After I get the black screen and I have to reboot. I am using Ubuntu 11.04 (64bit)

Here are the full specifications (I think that you should know about):
[B]
ASUS K72JT-TY165D[/B]
-----------------------------------------
 [Intel]("http://www.evomag.ro/vizualizare_cuvant.php?idcuvant=41")® Core™ i5 Mobile 
 i5-480M
2660 Mhz
3072 Level 2 
 2400  (FSB)
-----------------------------------------
RAM  4096 MB 
 2x2048 
DDR3 1066MHz/PC3-8500 
-----------------------------------------
500 GB 
SATA
5400 RPM
-----------------------------------------
AMD Radeon HD 6370M
1024 
-----------------------------------------




Thank you!:)

You don't have the same problem as the OP since he is getting it during normal use while in your case I would guess that the machine is just suspending. Does a normal suspend/resume work on your machine?

---

### Post by Huss on 2012-01-06
Thanks for the quick replies imachavel and 2F4U. I will test now.

---

### Post by Huss on 2012-01-07
Memory ok, sleeps and suspends just fine, closing the lid just turns the back light off. The proprietary driver FGLRX was installed, I've removed it and see if that fixes the problem.

---

