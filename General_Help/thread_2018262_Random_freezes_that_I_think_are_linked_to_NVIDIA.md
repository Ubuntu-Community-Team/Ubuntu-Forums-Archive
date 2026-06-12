---
title: "Random freezes that I think are linked to NVIDIA"
date: 2012-07-06
forum: General Help
---

### Post by ulugeyik on 2012-07-06
Hello,

Last few weeks I have been experiencing a lot of random freezes of the GUI. Most of the times, it simply freezes (I can move the mouse etc) but I am able to even re-start lightDM or compiz or anything like that by ssh'ing into the machine. Sometimes, it logs me out and I can just log back in.


The only things I can locate are errors of this sort in the logs:

[  368.129632] NVRM: GPU at 0000:02:00.0 has fallen off the bus.
[  368.129648] NVRM: os_pci_init_handle: invalid context!
[  368.129650] NVRM: os_pci_init_handle: invalid context!
[  368.129672] NVRM: os_pci_init_handle: invalid context!


So I think it has to do with my NVIDIA card or its drivers. I have a G86, Quadro NVS 290 and I am running driver version 295.49.

The errors started when I was running 11.10 and I have upgraded to 12.04 which did not change the result.

I have run memtest and I have been monitoring the temperatures but I do not see anything weird.

The freezes occur at random times but I have to be using things like firefox, mutt, viewing pdfs etc but I could not narrow it down to the usage of flash, java etc type of usual suspects. It does not freeze if I just let the system stand on its own for hours.


Any suggestions to solve this problem or how to go about debugging it would be really useful.

Thanks,

---

### Post by Redblade20XX on 2012-07-06
Usually upgrading leads to these types of problem. In my opinion, it is probably a carried over configuration file. So you can do a fresh install or look for any abnormal file.

Did you look into the Xorg.0.log?

Also isn't your card a legacy card?
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

Maybe you should be using one of those drivers.

- Red

---

### Post by ulugeyik on 2012-07-09
Hello,

Thanks. I do not think my card is listed there. I am suspecting the NVIDIA issue could be a coincidence because today one of my hard drives disappeared from the BIOS. I took the box to someone who can check if I have a power supply issue now.


Xorg did not return anything I can make sense of either :<

Turgut

---

### Post by ulugeyik on 2012-07-10
It does not appear that power supply is the issue. The hard drive had a bunch of errors that fsck could resolve probably because of all hard boots :<

---

