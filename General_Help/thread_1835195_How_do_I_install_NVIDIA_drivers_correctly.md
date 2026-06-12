---
title: "How do I install NVIDIA drivers correctly?"
date: 2011-08-28
forum: General Help
---

### Post by bradlees on 2011-08-28
After an extended battle getting Ubuntu working on my laptop, it seems that it has been done. I am using 10.04 and am able to boot by modifying the Grub to permanently stay on ¨nomodeset,¨ If this option is not set, then the screen freezes and I can only run in recovery. Although I am content to leave it as is, functional, I would like to install the correct NVIDIA drivers. I am not sure if the version that is found in applications-additional driver is correct or if a manual install would be better. If anyone can point me to a comprehensive walk through that applies to my graphics card or could tell me how to do it, that would be tremendous.

I have a GeForce Go 7600 card.

---

### Post by Wim Sturkenboom on 2011-08-29
Please be aware that nvidia and nomodeset are not necessarily related.

A couple of months ago I needed the nomodeset parameter to at least make the system boot more or less normal with a nVidia 8400 based card. After that the drivers from the repository (still) did not work when I tried them so I had to go for the nvidia driver.

One or two (kernel?) updates later and the system works without the nomodeset parameter; I have not tried to use the drivers from the repository with them (they might ro might not work).

---

### Post by Quackers on 2011-08-29
The nvidia-current (recommended) driver should be good for your card.

---

### Post by bradlees on 2011-08-29
thanks. I will post back with the results.

---

### Post by bradlees on 2011-08-29
Ok, so none of the three provided drivers work correctly.The recommended driver causes the screen to freeze with lines all across it. The earliest, 173 appears to work, but when I open firefox, it opens in the top left corner with no close, minimize or maximize bar, and cannot be moved or close. Also when I click on the desktop icon a message says my windows manager does not support show desktop button or are not running a windows manager.n

I am going to re;move now and try a manual install which I didn´t have much luck with....

---

### Post by Wim Sturkenboom on 2011-08-29
Did you try <alt><F4> to close firefox? I wonder if what you see is not some dumb compiz effect ;)

I'm happily living with the 260 driver from the nvidia site. Just be aware that kernel updates might require rebuilding the driver again. A small sacrifice to get a properly working system :)

---

