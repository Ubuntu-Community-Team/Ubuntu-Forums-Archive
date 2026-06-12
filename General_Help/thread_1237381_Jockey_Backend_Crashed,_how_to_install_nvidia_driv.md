---
title: "Jockey Backend Crashed, how to install nvidia drivers?"
date: 2009-08-11
forum: General Help
---

### Post by pat23_2007 on 2009-08-11
Hello, 

My new install went great, but when I try to install the Nvidia drivers from the restricted driver menu. I get told 

> "Sorry, the Jockey backend crashed. Please file a bug at:

  ubuntu-bug jockey-common

Trying to recover by restarting backend." 

and it does not install the drivers, How do I install the drivers since this has happened every time I have tried to install them so far.

---

### Post by bodyharvester on 2009-08-11
you dont install drivers, you update the kernel by going into the update manager in administration or preferences

- joe

---

### Post by pat23_2007 on 2009-08-11
> **bodyharvester said:**
> you dont install drivers, you update the kernel by going into the update manager in administration or preferences

- joe


I have already updated everything, and it still tells me when I click install restricted drivers that the "jockey backend crashed."

---

### Post by bodyharvester on 2009-08-11
doesnt the nvidia work fine already with the drivers it has? 

ive never heard of any issues concerning poor nvidia drivers,  integrated intel are the worst offenders

---

### Post by pat23_2007 on 2009-08-11
> **bodyharvester said:**
> doesnt the nvidia work fine already with the drivers it has? 

ive never heard of any issues concerning poor nvidia drivers,  integrated intel are the worst offenders

I haven't been able to install the driver yet, everytime I try to with the Install Restricted Drivers function it tells me that crashed message.

---

### Post by bodyharvester on 2009-08-11
do you play games or something? the drivers for all wares are provided in the updates, whatever drivers you require are certainly already being used by the kernel to communicate with your card

---

### Post by Josey on 2009-09-11
This is happening to me as well exactly as the author described.  This is a completely fresh install of ubuntu, the first thing I did was try to enable the nvidia driver in restricted drivers manager.  I don't want to use windows to game, please help.

Nvidia
Pci express
7300

9.04

edit: possible solutions below

> went to synaptic, re-installed jockey and jockey common,
rebooted, chose hardware drivers again, activated the nvidia drivers and
THIS time it installed correctly, without the crash.


and

> 1) Install nvidia drivers

sudo apt-get install nvidia-glx-180

2) Run nvidia config

sudo nvidia-xconfig

Reboot and you should be running the restricted Nvidia driver :)

I will try them and report results.

edit #2:

The second solution, installing with apt-get from terminal, worked perfectly for me and OpenGl extensions are now working.  Good luck!

---

