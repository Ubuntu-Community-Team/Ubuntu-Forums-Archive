---
title: "Opening .pdf Links with Evince"
date: 2010-01-12
forum: General Help
---

### Post by ali_bongos_dad on 2010-01-12
Whenever I click a website link to a .pdf I get this error message,

"Could not launch Adobe Reader 8.1.2. Please make sure it exists in PATH variable in the environment.
If the problem persists, please reinstall the application."

Even though there is no Adobe Reader installed on my p.c. 

I then have to right click the link and "Save link as ..."

How do I set the PATH variable so that Evince can open the document directly without first having to save the link?

---

### Post by Hallvor on 2010-01-12
Try setting /usr/bin/evince as path.

---

### Post by ali_bongos_dad on 2010-01-12
> **Hallvor said:**
> Try setting /usr/bin/evince as path.

How do I do that?

---

### Post by dgoosens on 2010-01-12
Edit > Preferences > Applications

look for PDF in the list and select the action you want...

---

### Post by ali_bongos_dad on 2010-01-12
> **dgoosens said:**
> Edit > Preferences > Applications

look for PDF in the list and select the action you want...

Thankyou very much. That works fine.
To think that I've put up with this problem for ages. I should really RTFM.

---

