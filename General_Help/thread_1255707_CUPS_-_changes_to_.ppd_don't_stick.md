---
title: "CUPS - changes to .ppd don't stick"
date: 2009-09-01
forum: General Help
---

### Post by ecowan on 2009-09-01
I want to print on non-standard paper sizes and correct incorrect sizes, e.g. Envelope #10.

I have discovered that if I add lines to /etc/cups/ppd/Stylus_CX3800.ppd just like those where I found the word 'Letter', I can see the new sizes, and they work. Until I reboot or turn the printer off and on again, when CUPS seems to regenerate the .ppd file.

I have a temporary work around, by saving a copy of the .ppd and just copying it back after a reboot. But it's a real nuisance, especially since my printer is on my 'server' machine, and it shuts down automatically every night.

I have not been able to discover where CUPS keeps the template for the .ppd.

Anyone?

thanks. - Erny

---

