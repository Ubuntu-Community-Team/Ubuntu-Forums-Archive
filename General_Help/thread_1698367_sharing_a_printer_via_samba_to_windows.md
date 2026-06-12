---
title: "sharing a printer via samba to windows"
date: 2011-03-02
forum: General Help
---

### Post by ilantal on 2011-03-02
I have a problem which is driving me crazy. I have 2 Ubuntu 10.10 systems, a laptop and a desktop. I have an old HP 930C printer which I want to be hooked to the desktop and shared via the LAN to the laptop.
In both cases if I delete the printer from Administration -> Printing I can plug in the USB cable and both systems will automatically detect it and it will work properly (locally).
What kills me if I use Administration -> Printing -> Add -> Network Printer -> Windows Printer via SAMBA -> Browse.., I will see WORKGROUP and see both of my computers. Here is the kick: if the printer is on the laptop it will appear when I click ILAN-LAPTOP. On the other hand if it is on my desktop, it will not appear when I click ILAN-MAIN.

This message I posted earlier. Here is the new twist. Yesterday I got an update and everything worked perfectly - I could see the printer over the LAN and print to it using a remote XP machine. Today I got another update, and guess what? It is gone again.

The problem seems to be with SAMBA and VirtualBox. On the laptop I have no VirtualBox and there I can always Browse... to the printer when I hook it onto the laptop. On ILAN-MAIN I have VirtualBox and with yesterday's update I could Browse... and use the printer over the LAN. Today there was a new kernel and the Browse... is gone again. It seems like person A is fixing it and person B is breaking it.

I would like to know if there are other people who can confirm this bug. What you need is sharing over the LAN and VirtualBox.

Thanks,
Ilan

---

### Post by ilantal on 2011-03-31
This morning 31.3, the update managed told me there were updates to be installed. Several were connected to SAMBA. After updating I am happy to say that the printer sharing is back alive. Maybe it will stay fixed this time around??? Let's hope for the best.

Ilan

---

### Post by crispy_420 on 2011-03-31
Mark as Solved?

---

### Post by ilantal on 2011-04-12
Sorry, not solved just yet. It worked for a week or so until I updated something which causes it to fail yet again. I hope it will work in 11.04 but I haven't yet tried 11.04.

Ilan

---

### Post by ilantal on 2011-05-01
I upgraded to 11.04 and there it seems to be working.

Ilan

---

