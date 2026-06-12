---
title: "MAJOR PROBLEM!! ATI driver resolution!!!"
date: 2010-01-18
forum: General Help
---

### Post by Ghost Hacks on 2010-01-18
OK so now I have Ubuntu 9.10 installed and fully updated on HP Pavilion a6223w desktop and I just installed the ATI driver for my ATI Radeon HD 2400 and now I can't see anything because for some stupid reason, and I mean stupid, the driver decided to default to a screen resolution that is too high for my 17" CRT Monitor.  Why the hell would the driver default to a screen resolution so high?  Almost all drivers default to 800x600 when a new driver is installed, not higher!  I am currently logged in to my desktop but can't see anything so any key commands (doubt there are any) that will help should work.  Please I need this fixed ASAP!

---

### Post by Ghost Hacks on 2010-01-18
BUMP before I go to bed.

---

### Post by Ghost Hacks on 2010-01-18
BUMP,  I used the Ubuntu repos driver, not the official one from ATI.

---

### Post by Grenage on 2010-01-18
I might be able to help you with a basic xorg.conf file, where we can specify the resolution.  I assume what has happened is that the adapter has incorrectly detected the monitor's capabilities.

If you press Ctrl-Alt-F1 to bring up a terminal, then log in.  Post the results of the following command:

```
lspci | grep VGA
```

Please also post your monitor make and model, along with the desired resolution.

---

