---
title: "Grub Rescue Error"
date: 2011-01-12
forum: General Help
---

### Post by ajputnam on 2011-01-12
Hello Everyone,

I am new to Ubuntu and I am trying to learn more about it. I have an HP laptop running windows vista. I decided I wanted to try Ubuntu. I got a live CD and Installed Ubuntu on an usb device through my laptop. I can boot Windows Vista and Ubuntu perfectly fine when the usb is plugged in. When I pull the usb out and start up my computer I can not boot Windows or Ubuntu with out the usb. I would expect not being able to run Ubuntu but would like my windows to run with out the usb. Is this a permanent configuration or can I some how change this?

[U]This what screen displays at boot  

[/U] error: no such device: ef56635b-772f-4149-9a61-3f33d688a94c.
grub rescue>



Any help would be Great!

---

### Post by sikander3786 on 2011-01-12
Welcome to the forums :-)

This means that you installed Grub to your USB drive accidentally.

Plug in your USB drive and boot from an Ubuntu Live CD/USB and post the otuput of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us exactly about your setup and thus help diagnose/solve the problem.

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by ajputnam on 2011-01-12
I got the problem fixed by fixing my MBR in windows and then re-installing ubuntu on my usb properly. Thanks for the Help, to bad I fixed it before I checked furm.

---

### Post by CarpKing on 2011-01-12
This happened to me when I was installing 10.10.  I booted with a live USB and installed to my hard drive, but apparently grub or the MBR or got written to the USV stick instead.  It would only boot normally with the USB stick in, otherwise I couldn't get to Ubuntu or Windows.  I had to reinstall grub, making sure I specified a partition that was actually on the hard drive.

---

