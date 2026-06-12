---
title: "Nvidia"
date: 2011-09-15
forum: General Help
---

### Post by Ibuntu-and-uIbuntu on 2011-09-15
Question about Nvidia drivers.... the computer I am running has a 1 gig graphics chip, yet Ubuntu is using the integrated Intell chip. I looked under synaptic package manager and I can't tell if the driver is activated. The driver is installed, but the "Drivers" menu says its not activated....How to go about doing this?

---

### Post by Frogs Hair on 2011-09-15
Hello and Welcome 

I also use Nvidia drivers and in my case on 11.04 the message is caused by a bug . If the driver was not activated Unity would not work on my hardware . The Nvidia X Server Settings are also installed and functioning .

---

### Post by grahammechanical on 2011-09-15
If this is Nvidia Optimus technology then you have a problem. The purpose of this technology is to allow software to switch between the on-board Intel adapter (low battery drain) and the discreet Nvidia adapter (higher battery drain) whenever there is a need for high power graphic manipulation, and then back again when the need has gone. This reduces battery usage compared to using the Nvidia adapter all the time.

Here is the problem. Nvidia cooperated with Microsoft to get the system working with a Pre-installed version of Windows. But has not produced a driver for Linux that works as well.

Things may have changed since I last read about this. So, if this is an Nvidia Optimus setup then you need to search for solutions for this specifically. Look for something called Bumblebee. I think.

Regards.

---

### Post by Ibuntu-and-uIbuntu on 2011-09-15
It does have the Optimus technology.....damn. I used to think it was cool, like my computer was a transformer with its "Optimus" technology, but this sucks. Ill look into bumblebee. Thanks for the replies and I'll post what I find. I overlooked that part of the graphics card while I was troubleshooting!

---

