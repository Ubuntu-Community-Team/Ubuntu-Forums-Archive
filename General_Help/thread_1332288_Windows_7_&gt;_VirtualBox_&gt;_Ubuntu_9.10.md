---
title: "Windows 7 &gt; VirtualBox &gt; Ubuntu 9.10"
date: 2009-11-20
forum: General Help
---

### Post by kindiboy on 2009-11-20
Hello, 

Am using windows 7 ultimate 64 bit
installed 64bit VBox
and installed Ubuntu 9.10(32bit) on VBox.

problem am having is the color depth problem it's stuck at 16bit
tried everything xorg.conf, reinstalled, changed the virtual display memory in VBox
nothing seems to cut it.

i also instelld the guest additions... i've looked into alot of threads regarding this issue 
no method seems to work...

need help

thanks,

---

### Post by darkksyde on 2009-11-20
Are your HOST graphics drivers installed?

---

### Post by P4man on 2009-11-20
as above. install the guest additions for ubuntu.

---

### Post by El Zoido on 2009-11-20
> **P4man said:**
> as above. install the guest additions for ubuntu.


I think he mentioned having already installed them.

Hm, I would check the settings of the virtual graphics adapter in Virtualbox, just in case.

---

### Post by kindiboy on 2009-11-20
thanks all

HOST drivers installed lol
guest additions installed

@El Zoido
the only two options are raising the memory and enabling 3d acceleration.
-------

help ^^

---

