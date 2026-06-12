---
title: "remote printer problem"
date: 2011-01-31
forum: General Help
---

### Post by ilantal on 2011-01-31
I have 2 Ubuntu 10.10 systems, a laptop and a desktop. I have an old HP 930C printer which I want to be hooked to the desktop and shared via the LAN to the laptop.
In both cases if I delete the printer from Administration -> Printing I can plug in the USB cable and both systems will automatically detect it and it will work properly (locally).
What kills me if I use Administration -> Printing -> Add -> Network Printer -> Windows Printer via SAMBA -> Browse.., I will see WORKGROUP and see both of my computers. Here is the kick: if the printer is on the laptop it will appear when I click ILAN-LAPTOP. On the other hand if it is on my desktop, it will not appear when I click ILAN-MAIN.

Why not?? What is different between the 2 systems that causes the printer not to appear in the SMB Browser (and of course I can't then use it via the LAN from my laptop).

Thanks,
Ilan

---

### Post by derklempner on 2011-01-31
> **ilantal said:**
> What kills me if I use Administration -> Printing -> Add -> Network Printer -> Windows Printer via SAMBA -> Browse.., I will see WORKGROUP and see both of my computers. Here is the kick: if the printer is on the laptop it will appear when I click ILAN-LAPTOP. On the other hand if it is on my desktop, it will not appear when I click ILAN-MAIN.

Why not?? What is different between the 2 systems that causes the printer not to appear in the SMB Browser (and of course I can't then use it via the LAN from my laptop).
Is Samba (**samba** and **smbclient**) installed on both systems?  Why are you using Samba to share a printer that's attached to an Ubuntu computer when you're trying to access it from another Ubuntu computer?

You can find more information on printer sharing in Ubuntu here: _[COLOR="Red"]https://help.ubuntu.com/community/NetworkPrintingWithUbuntu[/COLOR]_

---

### Post by ilantal on 2011-01-31
Yes, smbclient and samba are installed on both systems.

I failed to mention that my wife is using Windows XP and she wants to use the printer as well. I rarely print at all so I was mostly checking with my laptop to see what I could see. I would set it up while I was at it, but it is mainly for my wife's Windows machine.

Anything else that I could be missing?

Something else that may be involved: on the desktop machine I am using VirtualBox. Maybe that is doing something?

Thanks,
Ilan

---

