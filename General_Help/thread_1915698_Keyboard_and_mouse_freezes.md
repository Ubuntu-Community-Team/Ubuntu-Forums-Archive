---
title: "Keyboard and mouse freezes"
date: 2012-01-26
forum: General Help
---

### Post by carl79 on 2012-01-26
I have installed Ubuntu 11.10 on a computer without PS/2 ports, so I have connected an adapter that has a USB connector in one end and two PS/2 ports in the other end. This seems to function without any problems, but then suddenly the mouse and keyboard will freeze for one or two seconds and then work for 5-20 minutes and then freeze again. I can see the Num Lock LED turn off and on again when it happens. When the mouse unfreezes it wil somtimes move quickly to the top on the screen and do as if I was pressing the buttons really fast, so if I am browsing a webpage the everything the cursor touches is getting activated and higlighted. This is extremly annoying and almost makes the system unuseable. I have tried to change everything on the physical layer, mouse, keyboard, adapter, different USB port etc. but this makes no difference. There is no messages in any of the log files.  

Any suggestions on what I could try to fix the problem, or how I could monitor the USB port to gain more information when the freezes happen?

---

### Post by GraeW on 2012-01-27
it sounds like there is some sort of interrupt collision between the two devices through the one adapter? I don't know USB too well other than "plug it in and it works" but I know the old serial and ps/2 devices usually had to worry about IRQ Interrupts. Perhaps separating the two devices to different adapters can help? Otherwise I'm as stuck as you are on the answer.

---

