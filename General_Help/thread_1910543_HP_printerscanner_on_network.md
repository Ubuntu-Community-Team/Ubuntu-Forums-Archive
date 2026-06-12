---
title: "HP printer/scanner on network?"
date: 2012-01-17
forum: General Help
---

### Post by Docaltmed on 2012-01-17
I just installed the HP OfficeJet Pro 8600 printer/scanner as a network printer via its built-in wireless.

However, I have tried several scanning utilities, none work, and 

```
sudo scanimage -L
```

shows no attached scanners. 

How can I set the scanner up to be accessible via the network?

---

### Post by coffeecat on 2012-01-17
Have you enabled the ufw firewall in Ubuntu?

See that dent on my forehead? That's a result of wondering why my OfficeJet printer/scanner would work in Natty but not in Oneiric. Until the penny dropped, that is.

If this is a firewall issue, does printing work, and what ports have you opened? I discovered that HP uses some somewhat unexpected ports.

---

### Post by Docaltmed on 2012-01-17
lol coffeecat, I've got some dents in the same place!

I'm not using any firewall. Printing works with no problem whatsoever, so I'm thinking there isn't a blocked port. 


I can't figure out how to tell the scan software where to look for the scanner. I assume it's checking the USB ports and coming back empty-handed. I'm wondering if there is a way I can point the software to the right address?

---

### Post by coffeecat on 2012-01-17
Sorry - I don't think I'm going to be much help. I've been lucky so far. So long as I've set my network HP OfficeJet up for printing first, xsane "just works".

Just in case your Officejet is one of the few HP scanners that are not supported in Linux, have you tried connecting it via USB and trying a scan? At least that would exclude a network issue.

---

