---
title: "virtual box usb devices..."
date: 2009-08-20
forum: General Help
---

### Post by numbness05 on 2009-08-20
Hi guys.

I have recently install sun Virtualbox onto my Ubuntu 8.10 machine and install Windows XP as my guest (not something I am happy abut but needs must and all)

The reasoning behind this was literally to run the updates on my Tomtom sat nav (for which you need the Tomtom software which will not run under Wine unfortunately) and to install software to my Nokia 5800 which again needs to run through Windows and will not run under Wine.

So okay I have it working and actually quite liking the way XP runs on my 64 bit machine but wait... it doesn't show my USB devices...?
I have added myself to the Virtualbox user group in Ubuntu I have filtered the USB devices that I would like to use in XP am i missing any thing else any one?.

I am a complete novice with Virtualbox and to Ubuntu so if any one has any ideas please can you explain it as clearly as possible..

Thank you very much in advance any help would be massively appreciated..

---

### Post by yeeeev on 2009-08-20
You need to enable USB using  "Settings->USB->Enable USB controller"

---

### Post by Cheesemill on 2009-08-20
Bear in mind that the open source version of VirtualBox (the one in the default repositories) doesn't support USB.
 
You have to use the PUEL version available from the Sun website to get USB support.

---

