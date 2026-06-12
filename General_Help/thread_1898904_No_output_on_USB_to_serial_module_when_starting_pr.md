---
title: "No output on USB to serial module when starting programm as service during boot"
date: 2011-12-22
forum: General Help
---

### Post by sdrossaert on 2011-12-22
I have a c program, compiled en being started as a service on boot of Ubuntu 11. It makes use of a USB to serial module.

This combination of hardware and software worked on Ubuntu 10, but now i''ve ported everything to 11 is wont anymore

So whats the problem? : Whenever Ubuntu 11 boots, my service is being loaded and is running. However i dont get any output from the USB to serial module anymore

Whenever i restart the service (sudo /etc/init.d/<service> stop /start) it works fine. 
Also when i start the executable myself it also works fine.

I think the problem might has something to do with mouning the USB during boot or the serial port not being opend, however, i dont know how to check this.
I''ve mounted the USB to serial fixed as ttyUSB0.

Can anyone help me or give me tips where to look for?

thanks in advance

---

