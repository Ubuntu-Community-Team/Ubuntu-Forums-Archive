---
title: "My Computer, Memory and Ubuntu"
date: 2010-08-01
forum: General Help
---

### Post by netboom on 2010-08-01
Hey guys, I installed Ubuntu about a month ago and I'm loving it. I do however need to run a virtual box and I will be installing some software that is quite memory intensive.

My machine supports 4GB of memory so I'm looking at getting this

[B][http://www.maplin.co.uk/Module.aspx?ModuleNo=221756](http://www.maplin.co.uk/Module.aspx?ModuleNo=221756)

My machine says I can use the following
[/B]Each memory slot can hold DDR2 PC2-6400,DDR2 PC2-8500 with a maximum of 2GB per slot.*         

So first of, is that memory OK? also will Ubuntu recognise the 4gb?

oh BTW, I just did this. might help
darren@darren-desktop:~$ uname -a
Linux daen-desktop 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux

---

### Post by krishnandu.sarkar on 2010-08-01
Yes...But only if your OS is 64bit.

---

### Post by cascade9 on 2010-08-01
That memory should be fine. 

Ubuntu should have no problems with 4GB (or even a lot more) but you may need to install the PAE kernel (or renistall a 64bit version) to get all the RAM to work under ubuntu.

BTW, if you have more than 2 memory slots you can leave your current RAM in the computer and get more than 4GB (depending on what motherboard/chipset you have......I know, you said that your machine supports 4GB but that is pretty uncommon for DDR2 chipsets that support DDR2 800/1066)

---

### Post by netboom on 2010-08-01
Thanks guys, I only have two slots this is the computer

[http://uk.shopping.com/xPO-Acer-Aspire-M-3630-Intel-Core-2-Duo-E4500-Genuine-Windows-Vista-Home-Premium-2-1GB-RAM-250GB-SATA](http://uk.shopping.com/xPO-Acer-Aspire-M-3630-Intel-Core-2-Duo-E4500-Genuine-Windows-Vista-Home-Premium-2-1GB-RAM-250GB-SATA)

I'd rather not reinstall, I just got things the way I want them. How do I intstall PAE kernel and how likely am i to screw it up :) can it be done from the USC or SPM?

---

### Post by slooksterpsv on 2010-08-01
Most applications have 64-bit builds or equivalents. I'm running 64-bit Lucid Lynx and only 1 application I wanted to try, wasn't available, ZSNES, but oh well I have SNES9X.

I won't be going back to 32-bit anytime in the future.

---

