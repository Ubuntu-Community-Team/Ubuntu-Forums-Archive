---
title: "Ubuntu Doesnt Recognize USB Device"
date: 2012-03-19
forum: General Help
---

### Post by HTPro on 2012-03-19
So I have Ubuntu 11.10 x64 with VirtualBox ver4.1.2 With USB addons installed running Win7 x64 and I am trying to connect a URC Remote to program.  I do Custom Home Theater installations so programming these remotes is a must for me.  I cannot get the Win7 virtualbox to recognize the remotes when I plug them in USB and when I switch to Ubuntu and do lsusb I dont see them their either.  This leads me to believe the problem lies in my Host os not the guest.

I hope someone can shed some light on this.  The specific remotes im trying to connect currently are the MX-900 and MX-980 made by Universal. Both remotes work on other computers just not this one.

---

### Post by HTPro on 2012-03-19
I guess to add also, does Linux or Ubuntu use different packages to recognize various USB devices or are there settings within Ubuntu?

---

### Post by iiz on 2012-03-20
maybe some usb devices are in modprobe blacklist. you can check the blacklist files by looking in:
```
/etc/modprobe.d/
```
There is usually a few files in there and they are used to disallow certain devices like usb drives or input devices.

---

### Post by HTPro on 2012-03-20
The only thing I see in that folder related to usb is blacklist-cups-usblp.conf.  In there I see only a single line "blacklist usblp" not sure if I need that or not.

Also doing some more research and more testing I got the VirtualBox to identify the device finally now however It cannot connect to it to install the driver. I have the proper drivers for the device but it fails installation on the guest OS saying that the device is disconnected. When I do a "vboxmanage list usbhost" is says the current state is captured. Does this mean the host or guest OS has control of it? If it is the host how do I release it from Ubuntu so Windows 7 can do something with it.

---

### Post by varunendra on 2012-03-20
That seems to be some problematic printer driver, nothing to do with your issue.

Have you enabled "USB 2.0 (EHCI)" support in VBox? (requires the 'extension pack' to be installed).

---

### Post by HTPro on 2012-03-20
Yes I have enabled it and installed the extentions for Vbox. When I am inside the guest OS under the device menu in Vbox I can see my device, it is not grayed out and when I select it my Remote make a beep noise as it does when it connects to a computer however in the device manager nothing shows up and when I try to install the drivers for the device it says that the device is unplugged.

---

### Post by varunendra on 2012-03-20
Are 'Guest Additions' also installed on the guest Win7?

---

### Post by HTPro on 2012-03-20
Yes Guest additions are installed on the guest machine.

---

### Post by HTPro on 2012-03-20
Also I should mention I have added myself as a user to vbox.

---

### Post by varunendra on 2012-03-21
> **HTPro said:**
> Also I should mention I have added myself as a user to vbox.
Please confirm:
```
groups Your_User_ID
```
for example:
***groups varun***

Also, let's have a look at the output of:
```
lsusb
```
while the remote is connected to the computer.

USB connectivity in VBox has always been a headache for most of the users it seems. But you have already done whatever is usually required to be done. The VBox forum is full of such complains and possible solutions. Look in there if you haven't already.

If it is a problem of the host not allowing access to the guest (as you may already know, a USB device must be _logically_ 'disconnected' from the host before being connected to guest), you may try running it as 'root' from terminal:
```
gksu virtualbox
```
We may also get hints from the terminal if any error messages are left in it. However, be aware that any new files (e.g. new virtual disks) created during the root session will be owned by root, and thus would not be accessible by normal user.

You should also take a look at:
```
dmesg | tail -20
```
immediately after a failed attempt to connect. See if something related appears there.

As another alternative, you may try to install VMware Player which seems to be a bit more capable on handling USB.

---

### Post by HTPro on 2012-03-25
Thanks for the input, It turns out the problem was in the USB filter not setup properly. Fixed that fixed my problem.

---

