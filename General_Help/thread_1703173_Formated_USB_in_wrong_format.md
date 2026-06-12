---
title: "Formated USB in wrong format"
date: 2011-03-08
forum: General Help
---

### Post by Azirus on 2011-03-08
Windows wasnt detecting my USB memory stick (kept saying USB Device Not Recognized), but Ubuntu did read it so I decided to format the USB to try to get it to work on Windows again using mkfs -t vfat /dev/sda1 but instead of vfat I typed something else in by mistake (not sure what it was) now it doesnt work in Ubunutu either. It doesnt even show up under drives anymore. 
 
Any suggestions?

---

### Post by gerowen on 2011-03-08
You in a command line only environment?  If you have a GUI check the Ubuntu Disk Utility.  It doesn't have to be mounted to format the partition, it just won't show up in Nautilus.  If you want to do the command line you can just do:

```
mkfs.vfat foo
```

Where foo is the device location (/dev/sda1).

---

### Post by dcstar on 2011-03-09
> **Azirus said:**
> Windows wasnt detecting my USB memory stick (kept saying USB Device Not Recognized), but Ubuntu did read it so I decided to format the USB to try to get it to work on Windows again using mkfs -t vfat /dev/sda1 but instead of vfat I typed something else in by mistake (not sure what it was) now it doesnt work in Ubunutu either. It doesnt even show up under drives anymore. 
 
Any suggestions?

Use **gparted** or the Disk Utility to reformat it.

---

### Post by Azirus on 2011-03-10
I tried gparted but it doesn't show the USB and I am unable to find out the device location to do the mkfs.vfat foo.
 
Sorry kinda noob when it comes to Linux.

---

### Post by Azirus on 2011-03-10
I tried the Disk Utility as well but the USB doesn't show up in the list.

---

### Post by Hedgehog1 on 2011-03-10
When it gets this bad, you need to do a low-level format on the USB stick using a program from the manufacturer of the USB stick.

I hosed a couple of USB sticks until I got the hang of fancy partitions on them.  The low-level format fixed them all right up.

Hope this helps a little.

***The Hedge***

:KS

---

### Post by Azirus on 2011-03-10
Thanks for the tip I will try and look into it (the USB doesnt have a name on it its just silver :)).
 
I did run a "tail -f /var/log/messages" and when I put in the USB the results were as follows:
 
usb 2-1.1: new high speed USB device using using ehci_hcd and address 8
usb 2-1.1: new high speed USB device using using ehci_hcd and address 9
usb 2-1.1: new high speed USB device using using ehci_hcd and address 10
usb 2-1.1: new high speed USB device using using ehci_hcd and address 11
 
Not sure what that means though.

---

### Post by Azirus on 2011-03-26
I hope someone will be able to help me out with this problem, at this point its more just for knowing how to fix it incase the same thing happens again.
 
Thank you very much to everyone that has tried to help already and to anyone else that can provide some input :).

---

### Post by wanderingarticfox on 2011-03-26
I'm not sure this will help but do you see the USB 'devise' on your Ubuntu desktop? If  not unplug wait a minute and plug it in. If it shows the device on the desktop then right click and Format. If not then I bow out to others who know more.

---

### Post by linuxuser12345 on 2011-03-26
Plug in the USB device, and when the icon shows up on the desktop, right click and say "Format." A small popup should show up. Next to "Type:" on the right, choose "Compatible with all systems (FAT)." Label your device and click "Format."
Simple as that

---

### Post by Azirus on 2011-03-26
Thank you for taking the time to reply Fox , unfortunately I have tried that multiple times and in multiple computers to no avail (nothing shows on the desktop, gparted or Disk Utility). :(

---

### Post by linuxuser12345 on 2011-03-26
Just try formatting it in Windows. It should show up in Windows, but it will tell you it needs to be formatted.
It sounds like your USB device is trash now; No good. : /

---

### Post by Azirus on 2011-07-30
Windows wont recognize it either gives me the error "usb device not recognized one of the usb devices attached to this computer has malfunctioned" and the drive doesnt show up in "My Computer"
 
I guess I will retire this USB, thanks for the help everyone.

---

