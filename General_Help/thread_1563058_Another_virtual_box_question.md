---
title: "Another virtual box question"
date: 2010-08-28
forum: General Help
---

### Post by fidelandche on 2010-08-28
Ok,

 I have installed Virtual Box and XP with SP3 from an ISO and it works:D Now my Garmin Sat Nav (205W) still will not connect to the Garmin site:( I have installed the communicator plugin for IE but it still cannot find my device:( Is there something I have to do with VB to connect my Sat Nav via USB? or can I install USB drivers for the Sat Nav on my VM?

 Many thanks

---

### Post by spcwingo on 2010-08-28
Yes, you have to tell the guest system to capture it before booting and you also have to install drivers in the guest.  BTW, there is no USB support in the open-sourced version of VBox...for that functionality you need to install the PUEL(Personal Use and Evaluation License) version from Oracle.  If you need that version just visit their site for downloads or instructions on adding their VBox repository.

---

### Post by fidelandche on 2010-08-29
Ok thanks for that. How do I tell the guest system to capture it before I boot?

---

### Post by Vaphell on 2010-08-29
in the properties of your virtual machine go to the USB part and simply add a filter

---

### Post by fidelandche on 2010-08-29
Had a look for the USB part and I could not find it.

---

### Post by spcwingo on 2010-08-29
Then you're probably using the OSE (open-sourced edition) which has no USB support.

---

### Post by fidelandche on 2010-08-30
> **spcwingo said:**
> Then you're probably using the OSE (open-sourced edition) which has no USB support.

Downloaded the PUEL version from Virtual box, but however I cannot install it. I keep getting the error message that it conflicts with the OSE version, which I have uninstalled.

 Where do I go from here?

---

### Post by migs73 on 2010-08-30
Follow ALL the Debain instructions on this page [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) 

I had the same warning on trying to upgrade to a newer version, when just trying to download the .deb and install it.
Somebody else pointed out all the other stuff, and after doing that it worked fine.

BTW I don't have to select my USB before booting, just click on Devices--> USB Devices and check your device, which should be listed (if plugged in).

---

### Post by fidelandche on 2010-08-30
Ok, tried that but the OSE has not been removed when I removed it from the repos. I have also tried the link, but I think I must be doing something wrong because it would not install.

---

### Post by fidelandche on 2010-08-30
Ok,
I have now installed the correct version and added a filter for the USB, but When I boot up XP it still cannot find the Sat Nav. Is there anything else I have to do?

---

### Post by fidelandche on 2010-09-01
Ok,
When I click on devices the Sat Nav is unable to be ticked. I have added it as a USB device and added a filter but for some reason VB/XP does not find it, what can I do?

---

