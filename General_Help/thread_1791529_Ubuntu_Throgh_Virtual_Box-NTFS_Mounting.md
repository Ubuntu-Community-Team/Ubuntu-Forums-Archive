---
title: "Ubuntu Throgh Virtual Box-NTFS Mounting"
date: 2011-06-26
forum: General Help
---

### Post by navendranp on 2011-06-26
Hi,

I have installed Ubuntu 11.04 through Virtual Box. Working perfectly. Host OS Win 7 Home Basic (64 Bit)

Allocated Virtual Drive in Local Drive D with 12.5 GB Space.

a). I dont know how to mount NTFS drives (C & D) & access folders C & D and also from Thumb Drive & external HDD, from Ubuntu 

b). I dont know how to setup Networking of Ubuntu. I have changed the workgroup name as that of Win Network. My workgroup name is SYSTEM.

I would appreciate, some one helping me to resolve any one or both the issues mentioned above.

Thx/Rgds

Navi

---

### Post by howefield on 2011-07-01
> **navendranp said:**
> a). I dont know how to mount NTFS drives (C & D) & access folders C & D and also from Thumb Drive & external HDD, from Ubuntu

Which version of Virtualbox are you using ?

USB support is available with the addition of the extension pack, have you installed it ?


> I dont know how to setup Networking of Ubuntu.

Select Bridged in the network options for your VM, this will allow your Ubuntu guest to get an ip from the DCHP provider and appear as a separate computer on your local network.

---

### Post by navendranp on 2011-07-15
Hi,

Thank you very much for valuable guidance.

I have followed your instructions & I could see my Computer. See the pic below:

Screenshot-1.png

Even after entering the password to access my NTFS drives, I keep getting the pop-up. See the PIc below:

Screenshot-2.png

When I was trying to access the Windows Network, I get the following error message as per pic below:

Screenshot.png

Is there anything further needed to be done either in Unbuntu in VM or Host Windows O/S?

Thx/Rgds

Navi

---

