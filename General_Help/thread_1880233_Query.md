---
title: "Query"
date: 2011-11-13
forum: General Help
---

### Post by devarshi on 2011-11-13
hello friends ..m new ubuntu user.. i am really impressed with Gnome3 and wana install on my ubuntu system.

here is my pc configuration : 

   Operating System: Windows XP Professional (5.1, Build 2600) Service Pack 3 (2600.xpsp.080413-2111)
           Language: English (Regional Setting: English)
System Manufacturer: ATI___
       System Model: AWRDACPI
               BIOS: Phoenix - AwardBIOS v6.00PG
          Processor: Intel(R) Pentium(R) 4 CPU 2.66GHz
             Memory: 958MB RAM
          Page File: 426MB used, 1886MB available
        Windows Dir: C:\WINDOWS
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 5.03.2600.5512 32bit Unicode

1]will this System requirement be sufficient...for me to install Gnome3..plz reply 
2] If some problem comes with gnome3 will it be possible for me to get back unity interface.?? 

thank you ..waiting for reply

---

### Post by BillyBoa on 2011-11-13
Your computer specifications are close to ok.

To install Gnome 3 you have to download the package gnome shell

from a terminal

```
sudo apt-get install gnome-shell
```

Then log of and on the log on screen you have to choose GNOME instead of Unity. The selector is well hidden on a small wheel at the upper right corner of the name entry.

When you check Gnome 3 you can come back to Unity doing the same, log of, choose Unity and log on.

---

### Post by devarshi on 2011-11-13
Close to ok means will my PC show Slowdown of performance???

---

### Post by BillyBoa on 2011-11-13
Gnome 3 needs video accelerated graphics. But you could give it a try. If not the system will drop you to Gnome 2.

"The GNOME 3 desktop does require hardware accelerated graphics in order to provide a cutting-edge experience however, and the complete GNOME 3 experience will only be available on computers capable of this".

---

