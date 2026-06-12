---
title: "dvgrab Error no camera exists"
date: 2012-01-04
forum: General Help
---

### Post by test006 on 2012-01-04
Hi,
I am running kubuntu 11.10. I have been using dvgrab/kdenlive to capture video from my DV camcorder. I am using firewire port on my motherboard to connect to the DV camcorder. I have managed to capture some video but now when ever i run dvgrab i get error message "Error: no camera exists"
I am not sure what has changed since this was working fine couple of days ago.....
Please note i have always used 11.10 version to do all my capture so far.
Here are some of the output which looks normal to me from firewire stack view:
dmesg | grep firewire
[    1.460404] firewire_ohci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.460412] firewire_ohci 0000:02:00.0: setting latency timer to 64
[    1.524114] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x10

lsmod | grep firewire
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core

I am not sure how to troubleshoot this issue and why dvgrab cannot connect to my camera anymore....Any ideas please...


Thanks

---

