---
title: "Unable to get minicom to work properly with USB-&gt;serial adaptor"
date: 2010-07-18
forum: General Help
---

### Post by rgrover on 2010-07-18
Hi,

I am trying to get minicom to communicate with my development board over a usb->serial adaptor. The adapator and the development board work fine with Windows; and if I do a 'cat /dev/ttyUSB0' on Ubuntu (10.04), I am able to see messages like normal.

I ran 'minicom -s' to configure the serial port as /dev/ttyUSB0, and upon exiting the configuration menu I was able to see my serial messages fine; but when I restart minicom later, I get the following error:

minicom: cannot open USB: No such file or directory

Running 'minicom -s' to configure the serial device as /dev/ttyUSB0, and then exiting out of the configuration menu always works (however I notice that the serial device gets shortened to USB each time); but if I exit minicom after saving the settings and restart, I get the above-mentioned error.

Can someone please help?
Thanks.

---

