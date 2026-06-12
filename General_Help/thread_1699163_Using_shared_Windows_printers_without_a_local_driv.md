---
title: "Using shared Windows printers without a local driver."
date: 2011-03-03
forum: General Help
---

### Post by awp2513_ on 2011-03-03
Hi,

I'm a little shaky on how network/shared printing actually works, so maybe I'm asking for the impossible.

I have a Windows (XP) box that has several shared printers. I would like to be able to install drivers/modify printer options so that any Ubuntu box attempting to print to them doesn't need to have the printer driver installed locally.

Why don't I just go through the UI like everybody else, selecting the make and model, etc.? Well, It's a long story, but the short of it is that at the end of the day, I need to be able to add a printer using

lpadmin -p MySharedPrinter -v smb://host/sharedprintername  .... without specifying a ppd file, and print to shared printers.

Is this possible? I managed to do this with a network printer (a printer hooked directly to the network via an ethernet cable, not going through a print server), but I'm not even sure why that was possible in the first place.

Any help would be appreciated. If there is a good explanation out there for how to do this or why it's not possible, I haven't been able to find it.

Thanks,

awp

---

### Post by mastablasta on 2011-03-03
> **awp2513_ said:**
> Hi,
 
I'm a little shaky on how network/shared printing actually works, so maybe I'm asking for the impossible.
 
I have a Windows (XP) box that has several shared printers. I would like to be able to install drivers/modify printer options so that any Ubuntu box attempting to print to them doesn't need to have the printer driver installed locally.

yeah i am also not sure this is possible.
 
networked printer is like a server on it's own so that might be the reason why it worked there. 
 
you could try to mount the printer via samba. i think you will still need some interface (probably CUPS) to achieve this.
 
Perhaps if oyu could somehow configure printer via CUPS in browser?! guessinghere. hopefully somone with more knwoledge can shed some more light. 
 
but in my troubleshooting it always came to this that printer drivers of some sort needed to be installed on client computer as well as th eone used as server.

---

### Post by Mark Phelps on 2011-03-03
> **awp2513_ said:**
> I would like to be able to install drivers/modify printer options so that any Ubuntu box attempting to print to them doesn't need to have the printer driver installed locally.

Having done this LOTs of times (shared and networked printers), I can say that the printer driver was ALWAYS required to be installed locally.  This was true in both home installations and company installations.

I've even done network printer installs using CUPS (in five different versions of Ubuntu) and again, a local printer driver was ALWAYS required.

So, I'm mystified as to how you could have installed a network printer without also selecting a printer driver.

---

### Post by awp2513_ on 2011-03-03
It looks like I'll have to find another solution.

> So, I'm mystified as to how you could have installed a network printer without also selecting a printer driver. 

Yes, I'm not sure how it managed to print to the network printer. I confirmed that I was going directly to the printer and not a print server sharing it.

Thanks for the information!

awp

---

