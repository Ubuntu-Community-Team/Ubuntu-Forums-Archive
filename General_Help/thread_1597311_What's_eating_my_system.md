---
title: "What's eating my system?"
date: 2010-10-15
forum: General Help
---

### Post by GuiGuy on 2010-10-15
The following occurs in the Gnome and KDE desktops. I'm using 10.04 (AMD64). Kernel is 2.6.32-25-generic. The system has been fine for some time. The following started in the last 48 hours.

The hard disk traffic light on my PC is going non stop. I've killed most unnecessary processes but it makes no difference. I see that xorg CPU usage is hovering between 12% and 40%, with the system almost at idle.

Every now and then the desktop becomes briefly unresponsive. 

But the non stop trashing of the HDD seems a real worry.  

Any help anyone?

TIA

---

### Post by dino99 on 2010-10-15
watch system-monitor or htop to know about weird process, then into synaptic: remove/purge the blamed package then reinstall it

---

### Post by GuiGuy on 2010-10-15
> **dino99 said:**
> watch system-monitor or htop to know about weird process, then into synaptic: remove/purge the blamed package then reinstall it

Hi,
I've done all that. As per my post, only xorg is showing up as doing anything substantial. 

Is there someway of telling what's read/writing to the HDD?

EDIT: I just noticed the smbd is showing minor cpu usage. Could that be it?
EDIT EDIT: Removed machine from network. The HDD is still trashing :(

---

### Post by lisati on 2010-10-15
Is your HDD getting full?

---

### Post by GuiGuy on 2010-10-15
> **lisati said:**
> Is your HDD getting full?

No. the boot drive is 320G and has ~90G free. The swap partition is ~11G and by all indications barely touched. 

I've rebooted several times but the activity restarts on the log in screen. 

I'm reminded of Windows and viruses and malware :(

EDIT: I'm going to trawl through the logs to see if there's anything that might give a lead.

---

### Post by GuiGuy on 2010-10-15
OK, is smbd maintaining some sort of traffic between the PC and an 8T NAS device on the network. The NAS device is rather slow, so whatever is happening is likely to take time. 

Do I let it run or should I be wary of something sinister?

TIA

---

