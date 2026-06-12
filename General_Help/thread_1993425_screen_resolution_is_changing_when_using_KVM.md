---
title: "screen resolution is changing when using KVM"
date: 2012-06-02
forum: General Help
---

### Post by YigalB on 2012-06-02
My screen/KBD/mouse are connected to two computers via KVM.
every time I switch from the Ubuntu to the other PC and back, the resolution is lost and I have to re-run the "displays" software, and accept the "new" resolution.

This is annoying.
Is there a way to maintain the resolution I prefer?

---

### Post by LinGNUbie on 2012-06-02
I too use an older 8-port KVM that does not pass information through correctly (usually mouse).  This is actually the failure of the PC to read the edid information directly due to the KVM being inline of the signal. My workaround was to be sure that each connected device has its own configuration set via an xorg.conf file. However in the world of KVM's it may be that the monitor is unable to immediately recognize the change in resolution from device to device, which is again related to the no information pass through of the KVM. Also some KVM's you can set different monitor types for each device manually. Maybe have a look at it's manual for more specifics.

---

