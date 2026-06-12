---
title: "USB reconnect not recognized"
date: 2006-05-31
forum: General Help
---

### Post by mbeierl on 2006-05-31
This is slightly different problem from other usb posts.  I am using

  Kernel 2.6.16 (custom compiled with Suspend2 support)
  Ubuntu 5.10

When I boot or resume from hibernation, any usb mouse plugged in before power on is recognized and usable.

If I disconnect the mouse, I get the following in /var/log/messages:

usb 4-1: USB disconnect, address 2

But if I connect a new mouse or reconnect the same one, there are no messages generated, the mouse fails to configure, and, of course, is not usable.

I've tried a few searches about usb failing to respond when a new device is plugged in, but can't seem to find anything that resembles this problem.

Any help or insights are greatly appreciated!

---

### Post by PriceChild on 2006-05-31
Its got to be the fact that you've compiled your own kernel... I've always had many problems with them. Not worth the effort in my opinion.

---

### Post by mbeierl on 2006-05-31
I wanted proper software suspend support.  For some reason I could not get suspend to work properly with the stock kernel from breezy, so I used swsup2 instead, which required a patched kernel...

---

### Post by Ptero-4 on 2006-05-31
does hald, dbus and hotplug wake up from hibernation correctly? Those daemons are the ones that manage Linux plug&play functionality and if they fail, that would explain why the USB ports become unable to do hotplugging.

---

### Post by mbeierl on 2006-05-31
To the best of my knowlege they wake up correctly.  The mouse is recognized if I resume with it plugged in.  Just if I unplug it then put it back, I do not get a reconnect.

If I do a hotplug restart, it still does not recognize the device as plugged in.

If I then hibernate/resume, the mouse works once again.

---

### Post by Victor Von Doom on 2006-05-31
Iam getting a similar issue concerning disconnects iam using a iogear usb kvm switch and after switching from Ubuntu to my XP box and back the mouse stops responding. I dont think its the kvm switch due to the keyboard working fine. Iam new to Ubuntu so the only way i get it back is by Alt+ctrl+Backspace to restart X and relogin. Hoping for a fix here or some type of key command to wake the mouse ](*,)

---

### Post by mbeierl on 2006-06-02
Is it a usb mouse?  Have you tried unloading and reloading the usb HID modules?

Something like

sudo rmmod uhci_hcd ehci_hcd usbhid
sudo modprobe -a uhci_hcd ehci_hcd usbhid

For me, if my mouse stays connected, I lose "power" to the mouse (the optical light goes out) and mouse function stops on rmmod, and then comes back on modprobe.

My problem, I think, is related to my controller not waking up correctly after a hibernate/resume cycle.  I get 

[FONT="Courier New"]ehci_hcd 0000:00:1d.7: startup error -19
ehci_hcd 0000:00:1d.7: USB bus 1 deregistered
ACPI: PCI interrupt for device 0000:00:1d.7 disabled
ehci_hcd 0000:00:1d.7: init 0000:00:1d.7 fail, -19[/FONT]

in dmesg after the resume.  I've seen some posts on the suspend 2 mailing list about this...

---

