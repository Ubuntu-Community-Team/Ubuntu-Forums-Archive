---
title: "Bug with ubuntu and realtek nics?"
date: 2011-03-15
forum: General Help
---

### Post by millsy_c on 2011-03-15
Hey, been having a recurring issue on pc's I own with a realtek network card dual booting ubuntu 10.04 and windows 7.
In ubuntu the port is working fine (1000mbps duplex), but upon booting windows the network cable isn't detected despite the lights flashing on the nic.
Now I know this sounds like a windows question, but what I want to know, is if there is something that ubuntu can do to the nic that could cause this, and if so how on earth can I resolve it?
It effectively rendered my last motherboards lan port useless, and on my new system with the realtek nic I appear to have gotten the same issue.
And with it being a mitx rig, I have no room to add another lan adaptor in which I did in my last PC.
Suggestions would be greatly appreciated

---

### Post by plucky on 2011-03-15
Does it work when you boot windows from cold? i.e after a complete power off.

Has it ever worked in windows? 

Is it only after you reboot from Ubuntu?

What version of Realtek card is it? 

Post output of ```
lspci
``` from a terminal and maybe someone with your card can help.


Good Luck

---

### Post by Mark Phelps on 2011-03-15
Didn't notice what motherboard you have, but I have a new Gigabyte motherboard, which also has a Realtek nic, and it's taken two Windows driver updates and three months to get this problem solved.

Same situation as yours, only worse.  LAN works fine in Ubuntu.  Boot into Win7, LAN doesn't work.  Run Realtek diags.  Sometimes fixes the LAN, sometimes not.  Reinstall the Windows LAN drivers.  Sometimes fixes the LAN, sometimes not.

Sorry, but my experience is that it took Realtek two driver updates to finally get the LAN stable.

In the meantime, I bought a $20 Gigabit LAN card and used that.

---

