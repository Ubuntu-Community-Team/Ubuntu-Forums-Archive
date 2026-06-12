---
title: "Something is wrong with my graphics driver."
date: 2009-07-01
forum: General Help
---

### Post by theWrkncacnter on 2009-07-01
Can someone help me figure out what is wrong with my graphics driver? Desktop effects won't work and games are slow. What should I do first?

When I try to enable Extra visual effects, it searches for drivers, and then says "Desktop Effects could not be enabled." In the past I have been able to use desktop effects.

I'm using an nvidia geforce 7600gs. Thanks for your help.

---

### Post by LowSky on 2009-07-01
go to proprietary drivers under administration and enable the driver from there

---

### Post by colau on 2009-07-01
> **theWrkncacnter said:**
> Can someone help me figure out what is wrong with my graphics driver? Desktop effects won't work and games are slow. What should I do first?

When I try to enable Extra visual effects, it searches for drivers, and then says "Desktop Effects could not be enabled." In the past I have been able to use desktop effects.

I'm using an nvidia geforce 7600gs. Thanks for your help.
System>Administration>Hardware Drives

---

### Post by oldfred on 2009-07-01
I had the EVGA 7600 GTS card and also had issues. I never totally solved them because it blew it caps. I found that capacitors on the 7600 series are a common problem. Many others have had the same problem and some had pictures just like mine with the tops of the caps opened. In my case I heard a pop but the computer kept working so I was not sure what happened. Next morning no power at all on the system.
I believe my driver issues were that I had upgraded this computer from ubuntu 6.04 every version since and had tons of cruft left. I did find instructions on housecleaning everything before updating that helped, but never finished with the old card before the hardware failure.

---

### Post by theWrkncacnter on 2009-07-01
> **colau said:**
> System>Administration>Hardware Drives

The only driver in this section is the madwifi atheros drivers -- the display drivers aren't even in this section, so something is still wrong.

---

### Post by oldfred on 2009-07-01
You must not have the Nvidia drivers installed. In Synaptic check that under Settings tab for Ubuntu software you have checked the universe, restricted and mutiverse buttons. Then search for Nvidia and install the drivers. For you 7600GS card it should be the Nvidia 180.44 series of modules. I am surprised these were not automatically installed.

---

### Post by theWrkncacnter on 2009-07-02
> **oldfred said:**
> You must not have the Nvidia drivers installed. In Synaptic check that under Settings tab for Ubuntu software you have checked the universe, restricted and mutiverse buttons. Then search for Nvidia and install the drivers. For you 7600GS card it should be the Nvidia 180.44 series of modules. I am surprised these were not automatically installed.

I'm surprised too -- it had the 177 modealiases, but nothing else. I uninstalled those, and installed 
nvidia-180-kernel-source
nvidia-180-libvdpau
nvidia-glx-180
nvidia-settings
to see if that will help me.

---

### Post by theWrkncacnter on 2009-07-03
Alright, I have nvidia-glx-180 installed now, but I still can't enable desktop visual effects. When I try it says "Desktop effects could not be enabled." What's going on?

---

### Post by theWrkncacnter on 2009-07-04
...bump...

---

### Post by theWrkncacnter on 2009-07-04
I found a solution -- All I had to do was install nvidia-common. Then Hardware Drivers was able to detect the restricted drivers correctly, I chose 180, restarted, and now visual effects work.

Thanks everyone!

---

