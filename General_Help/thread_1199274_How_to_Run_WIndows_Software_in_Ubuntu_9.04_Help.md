---
title: "How to Run WIndows Software in Ubuntu 9.04 Help"
date: 2009-06-28
forum: General Help
---

### Post by K7RLW on 2009-06-28
I just installed Ubuntu Version 9.04 and have several software programs that are windows based.  How can I use these programs in Ubuntu ???   I need some help as need to utilize these programs.  Pleas explain in details how to accomplish this.  Thanks.

Rick

---

### Post by Tipped OuT on 2009-06-28
Well, what programs might they be? If it's something like MSN Messenger, or iTunes, then there's native replacement applications for these.

---

### Post by Newfoundlander on 2009-06-28
You need an application called Wine (which most people refer to as the Windows Emulator).

To install Wine, go to Applications>Add/Remove and type "wine" into the search box.  Put a tick in the check box and let it install.

Once installed, you can either double-click on your Windows program icon or right-click and select "Open with Wine".

Some software works with no problems, others need some settings tweaked to get them to work.  Visit [www.winehq.org](www.winehq.org) and and you'll probably find your software listed with tips, bugs, and info.

---

### Post by wojox on 2009-06-28
Wine is a translation layer (a program loader) capable of running Windows applications on Linux and other POSIX compatible operating systems. Windows programs running in Wine act as native programs would, running without the performance or memory usage penalties of an emulator, with a similar look and feel to other applications on your desktop.

[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by K7RLW on 2009-06-28
Thanks,

I judt downloaded Wine and set it up.  The software packages are installed and are running however I have a few minor or major issues.  The software packages are for Radio Communications Devices.  I am using an ICOM PCR1500 PC controlled scanning receiver and it is USB driven, The software starts and when I plug inthe receiver to the Computer I cant connect to the receiver, How can I use the USB ports to talk to my receiver, apparently Ubunto does not have USB drivers for my device.  

Thanks

Rick

---

### Post by Chronon on 2009-06-28
You may be better off installing Windows in a virtual machine (e.g. VirtualBox) and then installing your software and drivers there.  You might need the non-OSE version of VirtualBox to get USB functionality in the VM.

---

