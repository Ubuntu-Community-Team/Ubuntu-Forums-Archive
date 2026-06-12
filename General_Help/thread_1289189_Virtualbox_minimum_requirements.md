---
title: "Virtualbox minimum requirements"
date: 2009-10-12
forum: General Help
---

### Post by t0p on 2009-10-12
Due to the inadequacies of Wine, I plan to install Virtualbox on my Hardy-running desktop machine, with the intention of running XP within it.  But before I begin this task, I'd like to find out what the minimum specs requirements of Virtualbox actually are.

I've seen it claimed that to run Virtualbox requires a minimum of 512 MB RAM.  Is that a real-world requirement?  Or just a theoretical number?  My computer's specs are: 1 GB RAM, Pentium 4 32-bit 1.7GHz processor, hundreds of GBs disk space on an external HDD.  Will this be sufficient to run XP in a Virtualbox?  Oh, and will this instance of XP be able to use USB devices (specifically a mobile broadband HSDPA USB modem-dongle)?

---

### Post by GuyCorngood on 2009-10-12
I've run XP in VirtualBox on a machine similar to yours (but with 512 MB of RAM). It's a bit slow, but usable. What do you want to run in it?

And yes, VirtualBox supports USB devices (if you install the closed-source version). See [VirtualBox/USB]("https://help.ubuntu.com/community/VirtualBox/USB").

---

### Post by howefield on 2009-10-12
> **t0p said:**
> My computer's specs are: 1 GB RAM, Pentium 4 32-bit 1.7GHz processor, hundreds of GBs disk space on an external HDD.  Will this be sufficient to run XP in a Virtualbox?  Oh, and will this instance of XP be able to use USB devices (specifically a mobile broadband HSDPA USB modem-dongle)?

You should be ok with that, you need enough hardware resources to run both host and guest operating systems simultaneously. So your 1 gig of RAM will be split between the two according to your preferences and setup. Likewise the rest of your resources. 

As GuyCorngood said, for USB you need the PUEL (Personal Use and Evaluation Licence) version from the virtualbox website for USB support, rather than the OSE (Open Source Edition) edition in the repository.

---

### Post by 3rdalbum on 2009-10-12
Basically:

Host OS system requirements + guest OS system requires = Virtualbox system requirements

Since your host is Ubuntu and your guest is XP, your system should be enough. Just make sure you change the Virtualbox settings so your hard disk images get stored on the external hard disk.

Also note that the Virtualbox guest will see your host's internet connection as an "ethernet" device, so if your HSDPA modem works in Ubuntu then its connectivity will be available in XP automatically too. If your modem doesn't work in Ubuntu, then you will need the proprietary edition of Virtualbox available from the Virtualbox website, to give you USB passthrough support.

---

### Post by t0p on 2009-10-12
> **3rdalbum said:**
> 
Also note that the Virtualbox guest will see your host's internet connection as an "ethernet" device, so if your HSDPA modem works in Ubuntu then its connectivity will be available in XP automatically too. If your modem doesn't work in Ubuntu, then you will need the proprietary edition of Virtualbox available from the Virtualbox website, to give you USB passthrough support.

Okay, I see.  The modem *does* work in Ubuntu; but I want to run XP so I can use a piece of software written for Windows that will enable me to sim-unlock the modem.  I tried it in Wine, but it was a no-go (it couldn't see the USB modem).  So I will need the closed-source version of Virtualbox.  Good to know.  

Thanks for the info everyone!

---

