---
title: "Which Virtual Box?"
date: 2010-06-18
forum: General Help
---

### Post by Irony on 2010-06-18
I'd like to install Virtual Box on my Lucid machine but am undecided as to whether to install the proprietary version or the open source edition (OSE).

I would like to VNC into a guest operation system of Windows 7 and so install ultra VNC on Windows 7.

Am I correct in thinking that only the OSE will allow me to do this?

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

> Closed-source features

The following list shows the enterprise features that are only present in the closed-source edition. Note that this list may change over time as some of these features will eventually be made available with the open-source version as well.

    * Remote Display Protocol (RDP) Server 

    This component implements a complete RDP server on top of the virtual hardware and allows users to connect to a virtual machine remotely using any RDP compatible client.

    * USB support 

    VirtualBox implements a virtual USB controller and supports passing through USB 1.1 and USB 2.0 devices to virtual machines.

    * USB over RDP 

    This is a combination of the RDP server and USB support allowing users to make USB devices available to virtual machines running remotely.

Open-source features

The following list shows the features that are only present in the open-source edition. The licensing conditions of the necessary libraries prevent inclusion in the full-featured product.

    * Virtual Network Computing (VNC) Server 

    This component implements a complete VNC server on top of the virtual hardware and allows users to connect to a virtual machine remotely using any VNC client.

---

### Post by QIII on 2010-06-18
If I am reading it right, it seems that way.  Doesn't it?

"The licensing conditions of the necessary libraries prevent inclusion in  the full-featured product."

Lawyers, no doubt.

---

### Post by Irony on 2010-06-21
> **QIII said:**
> If I am reading it right, it seems that way.  Doesn't it?
Its not particularly clear. For example may plan is to install putty, copssh and uvnc client/server on it - I don't see how licencing could affect that as they are opensource.

---

### Post by ks07 on 2010-06-21
> **Irony said:**
> Its not particularly clear. For example may plan is to install putty, copssh and uvnc client/server on it - I don't see how licencing could affect that as they are opensource.
I expect they only included VNC on the OSE because of the GPL, so they couldn't include it in a commercial product. Seems pretty cool that they even bother implementing it in the free version, imo.

---

### Post by philinux on 2010-06-21
I installed the version from their website.

---

### Post by JustinR on 2010-06-21
I've used OSE and the nonfree version and it doesn't really matter. You should be able to access your client from VNC or VRDP

---

