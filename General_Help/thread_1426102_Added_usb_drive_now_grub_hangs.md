---
title: "Added usb drive now grub hangs"
date: 2010-03-09
forum: General Help
---

### Post by micrond on 2010-03-09
I have been running Ubuntu 8.04 Server as a file share for a year now and everything has been great. I recently ran out of hard drive space and it was cheaper to buy a usb drive than to get a large capacity ide drive to run internally so I picked up a 1tb Western Digital MyBook USB drive.

The problem Im running into is when the server reboots with the usb drive plugged in grub hangs on "Please wait..." and never goes any further. If I unplug the usb drive and reboot, grub and ubuntu boot perfect.

There are a total of three drives in the system including the usb drive.

sda 10gb OS drive
sdb 120gb backup drive

sdc 1tb usb drive

Grub is installed on sda and set to boot the kernel on sda1 so Im not understanding why grub hangs with the usb drive plugged in.

I know the simple solution is to unplug the drive when I reboot but I like things to be automated and I have my computer set to power on after a power failure so If Im not home to unplug the drive it will just sit there.

Any help getting this issue resolved would be awesome!

---

