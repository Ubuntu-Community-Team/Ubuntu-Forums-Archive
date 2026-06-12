---
title: "Karmic IPP printing problem"
date: 2010-01-06
forum: General Help
---

### Post by jmb365 on 2010-01-06
I have an HP LaserJet-6L printer connected to a Fedora7 PC via parallel port.   It prints fine when printing to it either locally or from various other Ubuntu PCs running various versions of Ubuntu via IPP.  Only when printing from two recently installed Ubuntu Karmic PCs (which were Jaunty PCs), printing does NOT work. If there are any logs I need to attach, in this forum I will be happy to do so.

When submitting a job from either of these Karmic PCs, I see a window showing the job being submitted, with an associated job number, but it never shows up on the Fedora7's print queue (viewed at localhost:631 page).  The same task from any other Ubuntu PC (not at Karmic version) works fine!

I have tried several suggestions posted on these forums, but none have helped.  Upon reading many of the articles here it seems to me that IPP printing in Karmic is broken.  Any advice or pointers will be very much appreciated!

Regards,
JMB

---

### Post by jmb365 on 2010-01-12
Bump!

Would anybody help please?

---

### Post by mla12 on 2010-01-15
I experienced something similar... maybe it can help you.

I have a desktop machine with a locally attached printer configured for network printing. From my old laptop running Jaunty, no problems configuring and using it.

I got a new laptop for Christmas and installed Karmic. I brought up System > Adminstration > Printing, and clicked the "New" icon. It searched for a bit and brought up a "Select Device" screen with a "Network Printer" section. I clicked it and it did seem to find the network printer. However, printing was screwed up. It also listed a "Internet Printing Protocol (IPP)" option, but no matter what I entered, the "verify" button was greyed out.

Anyway, tonight I gave it another try. Instead of clicking the "New" icon, I went into Server > Settings and clicked the "Show printers shared by other systems" checkbox and clicked "OK." Then I clicked the blue arrow icon thinking it would refresh the printer view, but it didn't seem to do anything. I closed the printer configuration and then went back to it (System > Administration > Printing) and the network printer was shown. I selected it and printed a test page successfully.

Jaunty seemed to be easier to configure but I don't really remember what it involved.

Hope that helps.

---

