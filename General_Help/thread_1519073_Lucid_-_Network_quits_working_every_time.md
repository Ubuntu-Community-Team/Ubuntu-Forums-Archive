---
title: "Lucid - Network quits working every time"
date: 2010-06-27
forum: General Help
---

### Post by sumpm1 on 2010-06-27
Hello guys. I didn't quite know how to describe my problem in the title. I installed Lucid i386 on my wife's PC two days ago. I updated all programs from the update manager. This PC uses a usb Wifi adapter for internet. When I boot the PC, the internet works. But after one or two hours, the networking capabilities disappear. In the network list in the panel there are NO networks listed, and the only way that I have been able to restore the ethernet is to restart the PC. What can I do to correct this?

If you need to see the output of any commands, please let me know.

---

### Post by cariboo on 2010-06-27
More details would help, what make/model/chipset is the device, is it using the proper driver?

---

### Post by sumpm1 on 2010-06-27
The wireless adapter is a Zonet ZEW2500P and I have used without a hitch with no driver install for the past year on 9.04. But since installing Lucid, the network works fine on startup for an hour or so and my network as well as 3 of my neighbors's wireless networks appear in the network list, after an hour or so, the network list disappears from the network applet, and the list is empty. Upon system restart everything works again for another hour! But I have had no problems with the device for the past year under Ubuntu as I said, and the device works without error when it is working.

Like I said, if there is any command that you could gather data from the report, just let me know the command.

Thanks

---

### Post by bollix47 on 2010-06-27
No idea if the following is in any way connected to your problem but have you looked into using usb-modeswitch?

From the sticky "Known Lucid Lynx issues/bugs with workarounds":

> Problem with Huawei and **possibly other usb mobile broadband dongles.**
Please see this bug report and click the affects me button if you have this bug.
Try this first
Code:

sudo apt-get install usb-modeswitch

A fix is committed. [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/446146](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/446146).
Also fix/workaround here. [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/509547](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/509547) See post #32


---

