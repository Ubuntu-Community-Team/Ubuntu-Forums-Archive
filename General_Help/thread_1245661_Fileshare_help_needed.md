---
title: "Fileshare help needed"
date: 2009-08-20
forum: General Help
---

### Post by chriscross93 on 2009-08-20
Hello,

I have an ASUS EEE PC 1000HE running UNR Jaunty.  My problem is that its shared folders cannot see or be seen by other computers on the network.  I have another laptop running regular Jaunty wirelessly and dont have this problem.  Does anybody have any idea what I need?

Thanks.

---

### Post by snotplop on 2009-08-20
Do you have samba installed?

Check for the package "samba" using synaptic.

If it is, see if you can at least list the shares on the other machines in the network by opening a file browser (nautilus, not firefox!) and typing in ```
 smb://ip.address.of.machine
``` into the Location: bar.

Provided the machines are indeed networked, it should either list the shares immediately or ask you to authenticate and then list the shares depending on your settings.

---

