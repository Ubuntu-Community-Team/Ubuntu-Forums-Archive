---
title: "VirtualBox 3.2.10 can't access USB ports"
date: 2010-11-22
forum: General Help
---

### Post by daldude on 2010-11-22
I installed VirtualBox 3.2.10 running Windows XP Pro and I don't have Access to my USB Ports in XP. VirtualBox shows the ports but they are grayed out and XP device manager lists 
Intell 82801FB/FBM USB2 Enhanced Host Controller - 265C
Standard OpenHCD USB Controller
USB Root Controller
USB Root Controller

under device manager but when I click the USB Root Ports it shows nothing attached and says that there are 8 ports available in each HUB.
If I plug in a device Windows does not detect a new device or report any kind of errors about USB devices and there are no yellow exclamation points under Device Manager. 

The online help is not much help all it says is to add a filter and I did that but still no access to my USB devices in XP.

---

### Post by Verbeck on 2010-11-22
you should install the guest additions
also add your name to the user group '[I]vboxusers' (system>administration>users and groups>manage groups)
[/I]

---

### Post by daldude on 2010-11-22
> **Verbeck said:**
> you should install the guest additions
also add your name to the user group '[I]vboxusers' (system>administration>users and groups>manage groups)
[/I]

**Update**

I did what you said I added my Linux User name to user group *vboxusers and at first it did not work and I said "damn it it still does not work"* so I rebooted Linux and low and behold when I loaded VirtualBox XP started to detect all my USB Devices and now I can finally use my Visioneer Flatbed Scanner withoit having to reboot to XP and wait the 7 minutes it takes for it to fully boot XP. Now XP takes about 1.5 minutes to fully boot under VirtualBox.

Thanks for your help.

**Old Problem below has been Fixed (So Far)**

I did install guest services and even tried it again in safe mode and Windows still does not detect any devices attached to the USB ports.

By the way that seamless mode is Cool, it's neat having a Windows XP  and a Linux Window on the same desktop. It's a poor mans Mac.

---

### Post by mountain_goat on 2010-11-23
Wow, thanks, this post really helped me too.
Fresh install of 10.10 after backing up my virtualbox XP Sp3 image to another drive.
Then with the latest VirtualBox I also could not access my USB software dongle thingy, which I desperately needed working for an on site visit tomorrow morning.
Added myself to the Vbox users, rebooted and hey presto, I can see my USB highlighted and not greyed out anymore.
Pheww, thanks again ;)

---

