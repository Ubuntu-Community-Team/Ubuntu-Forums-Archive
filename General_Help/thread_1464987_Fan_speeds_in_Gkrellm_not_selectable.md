---
title: "Fan speeds in Gkrellm not selectable"
date: 2010-04-28
forum: General Help
---

### Post by ahnilated on 2010-04-28
Hello everyone,

I am having an odd problem.  I can't get Gkrellm to show my fan speeds anymore since reinstalling Ubuntu.  I have tried 9.10 and 10.04 and tried installing packages to maybe get the drop down to show up for fan speed but still nothing.  I have installed Xsensors and that shows fan speeds correctly but I want to show them in Gkrellm like I used to have.

My system:

Ubuntu 10.04 with all updates
Intel i7 920 at 3.8G 
Asus P6T Deluxe V2 (bios 1003)
12G Corsair ram, 7-7-7-20, 1600Mhz
750 watt power supply
6X Noiseblocker 120mm fans. 2 on CPU heatsink, 2 pulling air in and 2 pushing air out.
Nvidia 250GTS video card
3 HD's.

Now every other temp gauge is working like it used to but the fan speed monitor.

Any tips/thoughts would be greatly appreciated.

---

### Post by Linuxforall on 2010-04-28
sudo apt-get install lm-sensors
sudo sensors-detect
select yes to all the options and enter when asked
reboot and your sensors will be back.

---

### Post by ahnilated on 2010-04-29
> **Linuxforall said:**
> sudo apt-get install lm-sensors
sudo sensors-detect
select yes to all the options and enter when asked
reboot and your sensors will be back.


Thanks for the response but that doesn't help.  I have lm-sensors installed and done sensors-detect before and just did it again to make sure.  Anyone else have any other thoughts?

---

### Post by ahnilated on 2010-05-03
Anyone have any other thoughts?

---

### Post by Onesimus on 2010-05-11
You can not do this currently because gkrellm-i8k is not in the repositories.  I have submitted a bug in launchpad but it has fallen on deaf ears.

---

### Post by wilee-nilee on 2010-05-11
> **Onesimus said:**
> You can not do this currently because gkrellm-i8k is not in the repositories.  I have submitted a bug in launchpad but it has fallen on deaf ears.

i8k is for dell computers, and it is in synaptic on Karmic and Lucid.

---

### Post by ahnilated on 2010-05-11
Ok, so it appears this is a bigger problem then what I first thought.

---

### Post by HobbitTR on 2010-05-23
> **wilee-nilee said:**
> i8k is for dell computers, and it is in synaptic on Karmic and Lucid.
18k is not in the Lucid repositories. According to the notes under i8kutils (utilities for Dell Inspiron and Latitude laptops)
The programs require the kernel module i8k.o which can be compiled from the package sources **or found in Linux kernel 2.4.14 and later versions.**

---

