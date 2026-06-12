---
title: "Which usb joystick for Ubuntu?"
date: 2012-01-25
forum: General Help
---

### Post by rva1945 on 2012-01-25
I need one for a game that runs in W7. Do you know of a compatible usb joystick that will work?

Thanks

---

### Post by jim_deadlock on 2012-01-25
[This thread]("http://ubuntuforums.org/showthread.php?t=1896223") might be of interest. The general concensus is that more or less any regular controller should work fine. I bought a standard Xbox controller and it's great.

Any problems are more likely to be down to the coding of the game itself rather than OS.

---

### Post by rva1945 on 2012-01-25
> **jim_deadlock said:**
> [This thread]("http://ubuntuforums.org/showthread.php?t=1896223") might be of interest. The general concensus is that more or less any regular controller should work fine. I bought a standard Xbox controller and it's great.

Any problems are more likely to be down to the coding of the game itself rather than OS.

Well, I configured it in Ubuntu. Jstest command shows all the buttons values (on-off or numeric values, depending on the Analog button setting).

But, the W7 running in a Virtualbox VM doesn't detect it. I even installed the driver that comes with the gamepad, but to no avail.

Do I have to tell the VM that there's a joystick running in the host system?

---

### Post by jim_deadlock on 2012-01-26
Yes you do need to enable it in your VM, there is a small USB icon at the bottom of the W7 window when you have it running, if you right-click it there should be a checkbox there to enable your controller. If not, you may need to install the extension pack and/or enable USB in the VM settings.

---

### Post by rva1945 on 2012-01-26
> **jim_deadlock said:**
> Yes you do need to enable it in your VM, there is a small USB icon at the bottom of the W7 window when you have it running, if you right-click it there should be a checkbox there to enable your controller. If not, you may need to install the extension pack and/or enable USB in the VM settings.

Hi:

The USB port is enabled as W7 detects the mouse no matter what USB port I connect it to. But maybe the mouse will always be detected.

As for the "USB icon at the bottom of the W7 window when you have it running", you mean an icon that appears as soon as I connect a USB device, like a pen drive?

---

### Post by jim_deadlock on 2012-01-26
This is the bottom of my Win 7 window, note the 3rd icon (USB)

[IMG]http://i932.photobucket.com/albums/ad168/jim_deadlock/vmusb1.gif[/IMG]

If I right-click the USB icon there's a checkbox to enable my game controller.

This is the USB settings for my Win 7 VM

[IMG]http://i932.photobucket.com/albums/ad168/jim_deadlock/vmusb2.gif[/IMG]

---

### Post by rva1945 on 2012-01-26
Thanks man!

Can't wait to arrive home and try it.
Are you using VirtualBox?

Thanks again,
Robert

---

### Post by jim_deadlock on 2012-01-26
Yes but the version from virtualbox.org website, not the one in the repositories (they are not the same).

---

### Post by rva1945 on 2012-01-26
> **jim_deadlock said:**
> Yes but the version from virtualbox.org website, not the one in the repositories (they are not the same).

And do you recommend that one instead of the one in the repositories?

---

### Post by jim_deadlock on 2012-01-26
Yes it has a couple of useful features that the open source one doesn't. Be sure to install the guest additions too.

---

### Post by rva1945 on 2012-01-26
Well, that's how I have the settings for the VM. The USB icon appears in W7, but if I right-click on it, I see these 4 disabled options:

DragonRise Inc generic USB joystick [0107]
ChiconyCorp Lenovo Easy Camera [2507]
A4 Tech USB mouse [0014]
Generic USB-2.0 CRW [5888]

(the same if I go to Devices->USB devices in the VM menu)

If I hover over the icon:

No USB devices attached.

Of course I checked that it's working in Ubuntu by running
jstest /dev/input/js0

So?

---

### Post by rva1945 on 2012-01-26
And I then added the filter in the VM settings; when I clicked the "+" button, I chose the Dragonrise Inc generic USB joystick; but it is still disabled in the VM.

---

### Post by jim_deadlock on 2012-01-27
Did you install virtualbox from the website, and did you install the extension pack?

---

### Post by rva1945 on 2012-01-27
> **jim_deadlock said:**
> Did you install virtualbox from the website, and did you install the extension pack?

Frankly, I don't remember how I installed it. I'l check the extension pack later (just in case, how do I install it, from synaptic?)

I tried in another PC at home but with a WXP as the guest and the gamepad was detected on the spot and it works fine in the guest.
Then I thought that the device is not compatible with W7, but the same problem happens if I plug a Kingston pendrive in the W7; it appears as disabled when right-clicking on the USB icon and will never be detected. Do you think that installing the VB extension pack will solve the issue?

And I could try copying the VM from one PC to the other.

Thanks

---

### Post by jim_deadlock on 2012-01-27
I'm no expert on this but my guess is that you have the repository version of virtualbox installed (via synaptic or software centre), which doesn't handle USB very well, hence the greyed-out icons.

My advice would be to uninstall your current virtualbox, then download your version from here:

[https://www.virtualbox.org/wiki/Linux_Downloads]("https://www.virtualbox.org/wiki/Linux_Downloads")

It's a .deb file so just double-click to install. After you've done that, download the extension pack:

[http://download.virtualbox.org/virtualbox/4.1.8/Oracle_VM_VirtualBox_Extension_Pack-4.1.8-75467.vbox-extpack]("http://download.virtualbox.org/virtualbox/4.1.8/Oracle_VM_VirtualBox_Extension_Pack-4.1.8-75467.vbox-extpack")

I think you can install it by dragging the file onto the virtualbox main window, or maybe just double-click it. Then import your old W7 VM (.vdi file) using the wizard and see if that works.

---

