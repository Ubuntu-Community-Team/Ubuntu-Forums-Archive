---
title: "Huawei EDGE Internet Modem EG162G"
date: 2010-05-19
forum: General Help
---

### Post by Zia371977 on 2010-05-19
Hi everyone,

I have recently switched from Windows to Ubuntu 10.04 LTS. I have a Huawei EDGE Internet Modem, model number EG162G. What would be the procedures to activate the modem in Ubuntu? :confused:

Please HELP!


Regards,

Zia

---

### Post by jarviser on 2010-05-19
> **Zia371977 said:**
> Hi everyone,

I have recently switched from Windows to Ubuntu 10.04 LTS. I have a Huawei EDGE Internet Modem, model number EG162G. What would be the procedures to activate the modem in Ubuntu? :confused:

Please HELP!


Regards,

Zia

With most recent Huawei modems there is no setup procedure - you simply set up a connection by right-click on the network icon, select Edit Connections, go to the Mobile Broadband tab and add a connection. 
I would choose the option that says the ISP is not shown ("I can't find my provider...") even if yours is there, and create a new one with the APN of your ISP (Google it if necessary).


Some Huawei modems need "usb-modeswitch" installed from synaptic package manager to prevent the embedded software from running.

Worst case, as it's EDGE, it may be too old to be recognized.

---

