---
title: "Weird printing &quot;issue&quot; with a Brother HL-2070N"
date: 2010-07-20
forum: General Help
---

### Post by hyper84 on 2010-07-20
Hi all. I'm having a weird printing issue with a Brother HL-2070N printer. It is connected to my wireless router and I installed it onto my macbook 2,1 with no issues. I guess Cups found my printer but used the 2060 driver as there was no 2070N driver? Anyway, I installed with the recommended settings and I can print fine, but when a print a document with multiple pages, my printer acts like each page is a new print job: it warms up, prints one page, and then pauses and acts like it is re-initializing, then prints the 3rd page and so on. Has anyone encountered this and/or found a workaround? I'm okay with it since it does print but it would be so much faster if it could print all pages at once. Thanks for your time and help.

---

### Post by plucky on 2010-07-21
> I guess Cups found my printer but used the 2060 driver as there was no 2070N driver? 

Use Synaptic Package manager and search for HL-2070N and you will find ```
brother-cups-wrapper-laser
brother-lpr-drivers-laser
``` Select both and install.The correct driver will now be available for your printer.

Good Luck

---

### Post by dcstar on 2010-07-21
> **plucky said:**
> Use Synaptic Package manager and search for HL-2070N and you will find ```
brother-cups-wrapper-laser
brother-lpr-drivers-laser
``` Select both and install.The correct driver will now be available for your printer.

Yep, they make all the difference with that model.

---

