---
title: "Set printer to Greyscale by default"
date: 2011-11-02
forum: General Help
---

### Post by npluis on 2011-11-02
Hi,

I'm using an HP Laserjet Pro (all-in-one) on my local network. I have changed the default settings of the printer to print in Greyscale (System settings -> Printing -> Properties) but whenever I want to print something I have to manually change it to greyscale again since the print dialog says it will print in Color.

Does anyone know whats wrong?

I'm using Ubuntu 11.10

---

### Post by plucky on 2011-11-02
> **npluis said:**
> Hi,

I'm using an HP Laserjet Pro (all-in-one) on my local network. I have changed the default settings of the printer to print in Greyscale (System settings -> Printing -> Properties) but whenever I want to print something I have to manually change it to greyscale again since the print dialog says it will print in Color.

Does anyone know whats wrong?

I'm using Ubuntu 11.10

Try opening the CUPS interface and changing it there.

From your browser,input into the address bar ```
http://127.0.0.1:631/printers/
``` and change the printer configuration.

Good Luck

---

### Post by npluis on 2011-11-02
Wow, never knew that was there. 

Unfortunately it doesn't help. The settings in there are the same as in system settings. I tried changing them in the webinterface but it doesn't stick...

Maybe I should delete the printer and add it again...

edit:
No, doesn't work. I removed all printers and added only this one but still I can't save the settings. It doesn't matter if I print from Thunderbird, Firefox, OpenOffice, etc....

---

