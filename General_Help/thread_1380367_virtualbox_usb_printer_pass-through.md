---
title: "virtualbox usb printer pass-through"
date: 2010-01-13
forum: General Help
---

### Post by neilblue on 2010-01-13
Hello,

I am running ubutnu 9.10 with virtual box 3.0.10. Most of it is running smooth and I have my mustek (windows only) scanner working via vista in virtual box. Now I would like to connect directly to my epson printer from the vista guest, but the USB share option is greyed out for the printers. I guess because they are being detected in Ubuntu first. Does anyone know how I can get Ubuntu to pass the USB printer to the guest?

Thanks
Neil

---

### Post by monicamaria on 2010-04-09
Here are the steps that worked for me to get Virtual Box to recognize my USB ports:
 
 On the desktop:
  Menu System > Administration > Users and Groups
 Click the keys to make changes, type password
 Highlight you, the user, then click Properties
 Under the "User Privileges" tab, scroll down and check the "Use Virtual Box" 
 Click OK, then close.
 
 Hope this helps.
 
 Monica

---

