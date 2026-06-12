---
title: "NEC uPD720200 USB 3.0 (Express Card 34) Driver"
date: 2011-02-08
forum: General Help
---

### Post by cyanide on 2011-02-08
Hi all,

       I have just got the USB 3.0 expresscard as a gift. The express card has a NEC uPD720200 chipset. I would like to know whether this card has drivers in Linux and if it is, where to find the instructions. 

       I tried sliding it into the express card slot and running "lsusb" in the terminal but I could not detect the attached usb 3.0 or any usb 2.0 external hard drive.

Any help is appreciated.

Thanks.:p

---

### Post by cyanide on 2011-02-10
!!Bump!! 

Can anyone please help me with this issue??

Thanks.

---

### Post by cyanide on 2011-02-12
!!Bump!! 

Can anyone please help me with this issue??

Thanks.

---

### Post by EveryWhere on 2011-02-16
I'm using it on Ubuntu 10.10 x64, it's working for me.
The problem is that, everytime I reboot my notebook, my hard disk isn't detected anymore and I have to unplug/plug it again. This does not happen if I use the USB 2.0 port, so it seems to be related to the PCI-e card.

---

### Post by cyanide on 2011-02-20
Did u install any drivers or did it automatically detect the express card??

---

### Post by Dngoins on 2011-02-22
It works for mine, however I don't know if It's actually usb 3.0 or 2.0 because the speeds appear to be the same.

I have Ubuntu 10.10 x64 SuperSpeed 3.0 2 port PCI Express Card.

I just plugged it in and it worked. One thing I notice though, if I start the OS without it in, it's not available if I plug it in after the system is started; it's not plug n play friendly. Thus I need to plug it in before I start the OS.

---

### Post by cyanide on 2011-03-12
> **Dngoins said:**
> It works for mine, however I don't know if It's actually usb 3.0 or 2.0 because the speeds appear to be the same.

I have Ubuntu 10.10 x64 SuperSpeed 3.0 2 port PCI Express Card.

I just plugged it in and it worked. One thing I notice though, if I start the OS without it in, it's not available if I plug it in after the system is started; it's not plug n play friendly. Thus I need to plug it in before I start the OS.

Thanks for your info Dngoins. I tried it in Ubuntu 64 bit and works perfectly. Thanks a million for your help.

While I have yet to try it in Ubuntu 32bit, Ill be changing the label of this thread to "SOLVED".

Best Regards.

---

### Post by Alistair George on 2011-05-11
One thing to check is that some Motherboard have a series of jumpers which either enable external SATA, or PCI-E.
My ASUS P5VD2 is one of those. If you leave the jumpers at default which is usually SATA then the PCI-E expansion slot wont work!

Hope this helps someone.
Thanks,
Alistair.

---

### Post by Alistair George on 2011-05-18
> **Alistair George said:**
> One thing to check is that some Motherboard have a series of jumpers which either enable external SATA, or PCI-E.
My ASUS P5VD2 is one of those. If you leave the jumpers at default which is usually SATA then the PCI-E expansion slot wont work!

Hope this helps someone.
Thanks,
Alistair.

I have now tried 2 PCI-E USB 3.0 adaptor cards, but when they are in the slot the MBO will not boot. Suspect this MBO, or its incompatible with the card.

Also a comment from elsewhere: The USB 3.0 cards I have seen require a PCI Express 2.0 X 1 Lane, which is not what the old P5VDC-MX has.

---

