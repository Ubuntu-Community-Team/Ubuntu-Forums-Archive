---
title: "diable interrupt from interrupt line"
date: 2012-05-21
forum: General Help
---

### Post by utkarshrawat100 on 2012-05-21
I have kernel 2.6.28.11-genric #42-Ubuntu .I have installed my driver on  the interrupt line 11 .But I am founding there are other interrupt that  are being register  in this interrupt line .Other interrupts are when  we do 
```
cat /proc/interrupts output is 
ehci_hcd:usb1,ohci_hcd:usb2,CS5535 Audio,eth3,drvr1.
```drvr1 is my driver which I have built for this interrupt line . 
Can anyone tell how to remove all these above interrupt line i.e. ehci_hcd:usb1,ohci_hcd:usb2,CS5535 Audio,eth3

---

