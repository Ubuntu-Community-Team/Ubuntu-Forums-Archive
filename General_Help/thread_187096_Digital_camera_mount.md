---
title: "Digital camera mount?"
date: 2006-06-02
forum: General Help
---

### Post by Koybe on 2006-06-02
Hi there!

I had my digital camera automounting easily on my old fedora, but in dapper nothing appears and i can't even mount it by myself as there is not /dev device...

[quote="dmesg"][4298007.796000] usb 2-2: new full speed USB device using ohci_hcd and address 2[4298052.092000] usb 2-2: USB disconnect, address 2
[4298964.213000] ohci_hcd 0000:00:02.1: wakeup
[4298964.490000] usb 2-1: new full speed USB device using ohci_hcd and address 3[/quote]  /var/log/messages is telling the same.... I got not /dev/sd*
> ls /dev/sd*
ls: /dev/sd*: No such file or directory
 
I can just cry.... :) I searched other post but see nothing that helped me.

---

### Post by Koybe on 2006-06-02
My usb key and my usb hd aren't working neither.... Anyone got a clue on this? 

Thanks!

---

### Post by garyng on 2006-06-02
I don't see the usb-storage message, which is what handle these things. What you saw is just the USB system telling you that 2 devices are there, but it doesn't handle it automatically.

---

### Post by Koybe on 2006-06-02
Ok i tried to put on usbmount package but it doesn't change anything... so which package is use for usb-storage?

---

### Post by garyng on 2006-06-02
modprobe usb-storage

What I don't understand is that these are supposed to be handled by udev(hotplug in the past). If you already have this module loaded yet don't see the message, it means the module don't know about your device and you are basically out of luck.

Yet another reason why I use XP as the host as I never encoutered this kind of issue.

---

### Post by Koybe on 2006-06-02
Nice it's working now. It's just a pity it doesn't out of the box... 

Thank you garyng

---

### Post by givré on 2006-06-02
If it is not load at boot time (it's strange because it's done with me), you should had it to /etc/modules

---

