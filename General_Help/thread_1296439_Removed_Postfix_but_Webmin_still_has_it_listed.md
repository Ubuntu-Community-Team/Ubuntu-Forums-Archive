---
title: "Removed Postfix but Webmin still has it listed"
date: 2009-10-20
forum: General Help
---

### Post by MockY on 2009-10-20
I figured I would play around with Webmin on my virtual testserver just to see what the fuzz is all about. Please note that Postfix was installed during the time of the Webmin install, but later removed. I noticed that under Servers (in the Webmin GUI), Postfix Mail Server is listed, even though it is not installed. When I select the entry, Webmin tells me that it is infact not installed, but I can install it using APT. But why is it even there if it's not installed? 
Furthermore, I can tab my way to /etc/init.d/postfix , though nothing happens when I do a stop, start, or restart.

Could someone please enlighten me to why these two oddities are even possible when the software responsible for them is not even present on the system?

---

