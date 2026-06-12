---
title: "/home/me Where is my printer's info stored?"
date: 2010-05-30
forum: General Help
---

### Post by held7over on 2010-05-30
Ubuntu 10.04  Gnome

I have a hpDeskjet 940c. It ran great since 8.04 and still works great on 10.04.  However, I had to shut down the computer it is on to do some hardware repairs to the powersupply of the computer. 

So, I moved my printer to another Ubuntu 10.04 machine and discovered I didn't know the settings, such as baud rate, flow control, parity,  etc. Ubuntu had never asked me for them....nor was I lucky at guessing them. 

I then found the hp installer which said it supported my printer and would automatically do the install job, but after trying it, I found it only supported USB and my printer has only a parallel connection.

I then moved the printer to a 9.04 Machine, thinking I only needed to drop back in time, since my printer worked great during that era also, and discovered the same problem! Evidently my printer hasn't been supported for some time! Yet it has happily worked with each new version of Ubuntu.

This brought me to the realization there must be a file in my home directory which survives each new full install that I do, and that contains everything my printer needs to be automatically set up, as with each new version of Ubuntu, the wizard has worked great automatically setting it up. 

Does anyone know the name of that file, so that I can copy it to the new machine?

Thanks! :)

---

### Post by held7over on 2010-05-30
Maybe I should rephrase:  Each time I upgraded before, when I went to System/Administration/Printing to set up my printer, it started out by saying something like "SEARCHING FOR PRINTER" and it would find it and automatically set it up.

When I discovered this only happens on the one computer, and in the case of the other computers there is no automatic search for my printer and automatic configure, but instead I am presented with picking between a Series Printer or different forms of Network Printers and then tossed into a manual configuration page which is asking me info I don't know and haven't been able to google the results for, and then asked if I want to print a test page, at which point it never prints....I assumed there must be something resident on my first computer that tips the install apps to do a different routine?

If not, is there a tutor on how to configure one's printer information?

---

### Post by mike2357 on 2010-05-30
It appears that my printer configuration files are in the /etc/cups directory.

I did a clean install of Lucid on two computers recently and when I added the printer, it was a little slow but did add the printer after a minute or so.  The printer wasn't directly connected to either computer, but it's a wireless printer and is on my home network.

---

### Post by held7over on 2010-05-31
I tried renaming the cups file on the machine where I can't set up the printer, and tried ssh-ing a copy of my cups file from the machine that does work, but it complained it couldn't copy an SSL file that is included in the cups directory....

---

