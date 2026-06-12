---
title: "What's my watts? Measuring power while in Ubuntu"
date: 2011-04-11
forum: General Help
---

### Post by JohnnyC35 on 2011-04-11
I was wondering if there is a way to see how much power my computer is using while using Ubuntu. I know there are hardware devices, plugs, I can use but I didn't know if there was a computer program that I could use that would do the same thing. I am currently using an IONITX F-E, 2Gb 800mhz RAM, 6 Green WD 2TB drives, and plan on getting a blu-ray drive installed in the last slot. I am also using a PCI-E x4 SATA card, and using software raid 5. I have a 350 watt psu installed and would like to remove it and install a pico-psu but the pico seems to max out at 200 watts. Thanks for any info :)

---

### Post by Joe of loath on 2011-04-11
I'm afraid it might only be possible on laptops, but try this.

Install acpid, and powertop. Then run sudo powertop in a terminal, and it should show your power consumption. gnome power manager can also draw graphs of power consumption, among other things.

---

### Post by grahammechanical on 2011-04-11
I do not know of any program that will do this. I guess that you would still need some kind of physical connection to the mains power supply. What you could do is track down the specifications for the bits and pieces that make up the computer and see if the maker gives power usage information and add them together to see how much power the power supply would need to meet to requirements. Do not forget the CPU power usage. The faster the hard drives spin the more power they use. Your two HD are described as "green."  So, they should use less power than HD not described as green. You made a good choice there.

Regards.

---

