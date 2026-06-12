---
title: "Oneiric upgrade: System printing service not available!"
date: 2011-10-27
forum: General Help
---

### Post by taps on 2011-10-27
I recently upgraded my Toshiba NB305 to Oneiric via the update manager. Since then, I have not had access to my printer (networked HP OfficeJet Pro 7680). When I go to System Settings > Printers, I get the following message:

> Sorry! The system printing service doesn't seem to be available.

As a result, I can't add new printers (physical, cups-pdf).

I'm not very knowledgeable about Linux. I have no idea where to even start fixing this.

Any help would be much appreciated!

---

### Post by taps on 2011-10-28
In the end, I just removed every element of cups, together with configuration files, and installed from scratch. Did the job. This shouldn't be happening on upgrade.

---

### Post by GlammaGeek on 2012-04-06
> **taps said:**
> In the end, I just removed every element of cups, together with configuration files, and installed from scratch. Did the job. This shouldn't be happening on upgrade.

  I am running 64-bit Oneiric, and am having the exact same problem.  Neither is my OfficeJet L7780 being detected by the ppd files.  Although when I select "Manual" and input the IP address, it is found, then comes up with a yellow banner stating that the printer is not found. So, may I ask EXACTLY how did you uninstall everything?  To my knowledge, I've uninstalled everything I could, then reinstalled several times but the problem persists.  Thanks!

---

### Post by GlammaGeek on 2012-04-06
YAYYYYYY! I solved my own problem. I uninstalled everything I could through synaptic and reinstalled hplip-3.12.2.run. This got me to the point where I have been all friggin day.    So, I did a bit more research and found out the problem was that CUPS was not running or installed.  So, I installed CUPS by entering the following in a terminal:  sudo apt-get install cups  Simple, isn't it?  Anyways, now everything works and I got my officejet_pro_l7780 installed and scanning.    YAYYY ME!

---

