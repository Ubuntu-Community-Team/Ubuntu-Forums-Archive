---
title: "Software center/nm-applet/powermanager/desktop effects etc"
date: 2010-11-20
forum: General Help
---

### Post by mynthix on 2010-11-20
Hi, my problem is that the Network Manager icon aint showing, neither is the power manager. Im using "alt+f2" the nm-applet to get the NM work but removes after reboot, so i have to do this all time.. uhm, when trying to enable desktop effects is sats "searching for available drivers" and then "Desktop effects could not be enabled". When trying to install apps from Software center, neither of the apps installs, the button install just keep refreshing, but if i go terminal: sudo software-center im able to install everything. But i dont want to do that all freaking timee... Any suggs? 

Using ubuntu 10.10

thanks

---

### Post by mikewhatever on 2010-11-20
Can you post your computer specs - graphics, ram, cpu.

---

### Post by mynthix on 2010-11-20
> **mikewhatever said:**
> Can you post your computer specs - graphics, ram, cpu.

Msi cx600

Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz 3gb ram
M92 LP [Mobility Radeon HD 4300 Series]

anything more? ;o

---

### Post by mikewhatever on 2010-11-20
Well, the hardware seems alright, so check the following:

1. Nm-applet should be in the Startup Applications (under System->Preferences). Make sure it is there, and if not, add it using **nm-applet --sm-disable** as command.

2. You probably need a proprietary ATI driver to enable desktop effects. Is it installed? If not, try System->Admin->Drivers.

3. Not sure what's wrong with the Software Center. You could try the Synaptic package manager instead.

---

### Post by mynthix on 2010-11-20
> **mikewhatever said:**
> Well, the hardware seems alright, so check the following:

1. Nm-applet should be in the Startup Applications (under System->Preferences). Make sure it is there, and if not, add it using **nm-applet --sm-disable** as command.

2. You probably need a proprietary ATI driver to enable desktop effects. Is it installed? If not, try System->Admin->Drivers.

3. Not sure what's wrong with the Software Center. You could try the Synaptic package manager instead.

I've tryed all this but no result. And the drivers are activated. Could it have something with sudo? because im not able to click the "edit" button in Users and Groups aswell.. Is there anything like, something that checks all my files etc so they are not corrupted? Baah, hate this :(

---

