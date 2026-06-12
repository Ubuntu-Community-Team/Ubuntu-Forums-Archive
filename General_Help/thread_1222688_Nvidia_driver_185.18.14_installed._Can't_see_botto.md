---
title: "Nvidia driver 185.18.14 installed. Can't see bottom of screen"
date: 2009-07-25
forum: General Help
---

### Post by praveesh on 2009-07-25
Today I installed jaunty and installed nvidia driver 185.18.14 (GEFORCE 7300GS)which is got from their website . After rebooting, the monitor(1440x900 TFT LCD) automatically adjusted the display and the bottom portion of the monitor became not visible . The bottom panel of the Gnome and taskbar of windows is not visible. The problem exists only in widescreen resolutions(no problem in 1024x768 etc)  .Can any one please help me? This is the second time Iam installing the 185 driver . First I installed in KUbuntu jaunty. No problem . Then I formated the partition and Installed Ubuntu and installed driver and problem begun. The same problem occured one and half month ago, when I tried to change resolution in ultimate edition. It was yesterday that I got it after warranty replacement. Thanks in advance
NOTE: The attachment is created with GIMP. Original screen shot had bottom panel.

---

### Post by praveesh on 2009-07-25
The problem is rectified . Thank you

---

### Post by DeMus on 2009-07-25
> **praveesh said:**
> The problem is rectified . Thank you

How? What did you do? When you find the solution to your problem please let everyone know about it so people can learn from it. That is what it is all about: learning from each other.

---

### Post by praveesh on 2009-07-26
> **DeMus said:**
> How? What did you do? When you find the solution to your problem please let everyone know about it so people can learn from it. That is what it is all about: learning from each other.

OK. I don't know if it is the right way of doing. But it corrected the issue. I have an intel graphics media accelerator 950 too on the mother board. Nvidia is a seperate graphics card on the pci express slot. What I did is :

I shut the computer down. In the bios(hit del while booting) change the graphics to intel graphics media acceleraton (in my case, advanced chip set features->PEG/Onchip VGA Control->change from auto to onchip vga). Save by giving F10. Go to windows. Uninstall nvidia driver and Install Intel graphics media accelerator driver . Change the resolution to wide screen resolution to see if the problem persists or not. Still there's the problem. Reboot. No change. As a final attempt, install monitor driver(actually it's not needed to install . The monitor company says it) . No change. Reboot. Surprise !!!. Rectified. Again change the graphics to nvidia from the bios. Go to windows . Uninstall intel driver and install nvidia driver. Reboot. Change to wide screen resolution . No problem. Don't have courage to go to the corrupt Ubuntu. So freshly installed Ubuntu. Reboot . Installed nvidia driver (185.xx.xx using terminal). Reboot . No problem. Install nvidia driver in KUbuntu too . No problem.

What I think the problem is a communication problem between graphics card and the monitor . Actually the graphics card gave the full display. But the monitor displayed only top portion. Installing monitor driver rectified the problem

---

