---
title: "virtualbox-4.0 usb-2.0 pass through grey out"
date: 2011-01-01
forum: General Help
---

### Post by mathfeel on 2011-01-01
I have installed Virtualbox-4.0 as well as the extension pack using the instruction here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

I have also put my user in the 'vboxusers' group. But the usb-2.0 items are grey out and disabled. Help?

---

### Post by dgw on 2011-01-01
I had the same problem recently. I found that I had the Open Source Edition of Virtualbox installed (called Virtualbox OSE) and needed the non-open source version for USB support. I downloaded it from the Virtualbox website and installed. It's not at all obvious on their download page which you need, but I believe if you get the appropriate one from the list of .deb's on this page it'll work.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by mkupsta on 2011-01-02
I am having the same bloody problem, the devices are listed but all greyed out. I have most of the forum posts about resolving this issue and still cannot resolve the problem. I understand there is a difference between the OSE and PUEL version. I have installed the version from the website, which is version 4.0.0 r69151, by downloading the .deb file and then clicking on it which then brought up the package manager that allowed me to install VirtualBox. I also have also added myself to the vboxusers group. 
I am running 10.10.

---

### Post by JKyleOKC on 2011-01-02
For vbox 4.0 you have to download a second package to have USB support; it's on the vbox web site but apparently not anywhere else... Look for the "extension pack" to find it.

The PEUL vs OSE distinction only applied to 3.2 and earlier versions. At 4.0 the stuff requiring PEUL moved into the extension pack.

---

### Post by mkupsta on 2011-01-02
I have installed the extensions pack, I even reinstall to see if I managed to mess something up but I am still experiencing the same problem. They are still greyed out.

---

### Post by Vigh on 2011-01-02
your bios is not correctly configured to support virtbox4.0 usb, go into your bios and make sure multi-core processing and virtualization is enabled, fixed it for me, also if you have a quick boot option in the bios, untick it to make sure it loads up everything properly during the initial boot

---

### Post by mkupsta on 2011-01-02
I had a look at my bios, hardware virtualization was enabled. Multicore processing is enabled. I have an ASUS Striker II Formula bios version 1802 motherboard. I distinctly remember USB pass through working in 10.04.

None the less, your recommendation didn't work.

---

### Post by mkupsta on 2011-01-02
](*,)

Well now! So I finally got fed up, and uninstalled my previous version using Synaptic Package Manager (virtualbox-4.0 - mark for complete removal) and rebooted. Went to the virtualbox website, downloaded the deb file and doubled clicked on it. It ran the Ubuntu Software Center program, I click install and everything installed. I ran virtualbox, my .vdi of winxp was still there, and the FRIGGEN USB DEVICES WORKED!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Thank you guys, hopefully this helps someone too.

---

### Post by coldraven on 2011-01-03
All you need to do is reboot after adding yourself to the VBoxusers group. I presume you already installed the Guest Additions.

Search is your friend :) [http://ubuntuforums.org/showthread.php?t=1604549&highlight=virtualbox+tip](http://ubuntuforums.org/showthread.php?t=1604549&highlight=virtualbox+tip)

---

### Post by mkupsta on 2011-01-03
Believe me, I rebooted tons of times. Not just a logout, but a physical reboot.

---

### Post by sancheztavo on 2011-01-17
I'm having exactly the same problem. It worked with ubuntu 10.4 and VBox 3.2.
My machine doesn't support virtualization, so I can't enable that in my bios, as someone suggested...

---

### Post by garyjmellor on 2011-02-08
If I've understood correctly, I have got the VirtualBox OSE (4.0.2 r69518 ) application running on a Win7 64-bit host. I have a 32-bit Ubuntu Maverick guest. I have got my USB stick working fine but only via editing the guest OS's settings. So, to begin with, if you have your guest running, shut it down (don't save the state as doing so will not allow you to alter the settings - actually power it down).
 
Download and install the correct extension pack for your host (in my case this was Oracle_VM_VirtualBox_Extension_Pack-4.0.2-69518.vbox-extpack). Install this as follows:
 
1. In VirtualBox Manager, click 'File' > 'Preferences'.
2. In the left-hand pane, click the Extensions item (blue diamond icon).
3. In the right-hand pane ('Extensions'), click the 'Add' button (blue diamond with an upside-down orange triangle).
4. Browse to where you downloaded your extension pack to and click the 'Open' button. This should now install the extension pack and mark it as active (green tick) in the Extensions pane.
5. Click 'OK' to close the VirtualBox 'Settings' window.
 
Next...
 
1. In the VirtualBox Manager interface select your guest machine.
2. Click 'Settings' in the toolbar.
3. In the 'Settings' window that has now appeared, click the 'USB' in the left-hand window.
4. Ensure the 'Enable USB Controller' checkbox is checked.
5. Ensure the 'Enable USB 2.0 (EHCI) Controller' checkbox is checked.
6. Plug in your USB device if it isn't already attached to your host.
7. In the right-hand side, click the icon that looks like a USB plug with a green plus sign next to it (tooltip is 'Add Filter From Device').
8. You should be able to see you device in the pop-up that has appeared - select this.
9. Your USB device should now be added to the 'USB Device Filters' pane.
10. Click 'OK' on the 'Settings' window to save your changes.
 
You should now be able to boot your guest OS and see that the USB device is visible in it. In my case it was a USB pen drive. I did have a small issue of the host mounting the device first, which seemed to cause a problem initially (the guest couldn't see the device). A subsequent reboot sorted this out. The host would see the device first, then, when the guest was booted, the host lost ownership of the device and the guest then saw it. If you experience problems still, you can click on the USB icon in the bottom right tray on your guest OS and see what devices it thinks it has access to. If you see yours, click it. This will either mount it or give you an error message which you can further use to Google possible solutions.
 
I hope this has helped somebody.
 
EDIT: I forgot to add, my host machine does not support virtualisation (I wanted a 64-bit Maverick guest) but I still got this working. I did not need to add myself to the vboxusers group either and, as mentioned used the OSE not the paid-for version of VirtualBox.

---

### Post by Spyderkid on 2011-02-09
I don't have an extensions button...

---

### Post by balucio on 2011-02-24
Same problem!!!
I removed the ppa version and installed the DEB directly from oracle website and the usb now work. I also added my user to vboxusers group.

Tanks mkupsta

Saul

---

