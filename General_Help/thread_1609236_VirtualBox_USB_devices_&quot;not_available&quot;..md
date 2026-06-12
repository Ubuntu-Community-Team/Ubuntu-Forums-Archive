---
title: "VirtualBox: USB devices &quot;not available&quot;."
date: 2010-10-30
forum: General Help
---

### Post by t0p on 2010-10-30
I'm running the non-free version of VirtualBox, the one with USB support, on Ubuntu 10.04.  I have a guest XP running in VBox.

When I plug in USB sticks, then look at **Devices > USB Devices**, the sticks are there; but they are greyed-out, and when I mouse over them it says the devices are "unavailable".

Strange thing is, when I plug in my (USB-connected) HP Deskjet D2660, that *is* available.

I have image files on a USB stick, which I want to print via VirtualBox (I can't get the printer to work in Ubuntu).

Anyone know how I can get VirtualBox to use the USB sticks?

---

### Post by Suncoaster on 2010-10-30
Have you added yourself as a user to the vboxusers group.  Select System, Administration, Users and Groups, and add yourself as a user to the vboxusers group.

Hope this helps.

---

### Post by Irony on 2010-10-30
[http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12](http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12)

---

### Post by t0p on 2010-11-01
> **Irony said:**
> [http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12](http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12)

**Irony**:  Sorry it's taken me so long to get back to you.  Thanks for the link.  That solved my problem.  But I don't understand *how*.

It seemed to me that the tutorial would just enable me to share files between the Ubuntu host and the Windows guest.  Which it does, of course.  But it also made my USB devices available to the guest, and I just don't see how it did that.

But hey, thanks anyway.  I don't really *need* to know how/why it worked.  But I'd certainly *like* to know.

---

### Post by Irony on 2010-11-02
Yes I would like to know how too...

The [http://maketecheasier.com](http://maketecheasier.com) owner Damien notes the following

```
Few things you need to do to get your USB drive working:

1) Make sure you are not using the OSE version.

2) Upgrade your Virtualbox to the latest version 2.2.

3) Set up the USB filter in the Settings page. Make sure that the boxes “enable USB controller” and “enable USB 2.0(EHCI) controller” are checked.

4) Install Guest additions

5) Mount your USB drive in your computer before starting Virtualbox.

6) In your VM, go to Devices -> USB Devices and select the respective USB devices.
```

---

