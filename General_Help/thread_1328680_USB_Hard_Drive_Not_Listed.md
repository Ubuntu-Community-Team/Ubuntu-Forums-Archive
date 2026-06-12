---
title: "USB Hard Drive Not Listed"
date: 2009-11-16
forum: General Help
---

### Post by Bugs318 on 2009-11-16
Hi,

I have an external USB hard drive which worked fine on my previous desktop installation (8.04 - Hardy Heron) and continues to work fine on my laptop (also 8.04).

Having just purchased a new desktop and installing the 64-bit Karmic Koala (9.10), I was hoping to use this drive to transfer data to my new system.

However, while I'd previously used the commands 'sudo fdisk -l' and 'sudo mount -t vfat /dev/sdxx /mnt/external' to discern the mount point, and then mount the filesystem, the drive does not show up in the list following the first command such that I do not know which mount point to designate for the second command.

If I use the lsusb command, the device is listed, but it doesn't show the mount point (or the /dev location of the drive).

Can someone help me either figure out how to get the device listed in the fdisk -l command (as it does on my laptop) or else another way to discern the /dev/sdxx location of the device so I can mount it?

Thanks so much in advance!

---

### Post by audiomick on 2009-11-16
Hi. I'm afraid I can't help more than to say that there seems to be some weird stuff happening with USB in 9.10 64bit. Look around a bit. In the Installations and upgrades sections there has been a bit of traffic on this subject

---

### Post by Giblet5 on 2009-11-16
A mystery! Yay!

Open a terminal window and enter:

```
tail -f /var/log/messages
```

(It will not terminate until you hit Ctrl+C, but don't do that yet)

Now unplug the external drive.

Observe the messages.

Plug the drive back in.

Observer the messages.

Any useful clues there?

---

### Post by Bugs318 on 2009-11-16
Following your tip, Giblet5, The first command displayed the following that was absent in the second:

Nov 16 18:01:37 derek-desktop kernel: [ 6005.160026] usb 2-1: reset high speed USB device using ehci_hcd and address 14
Nov 16 18:01:47 derek-desktop kernel: [ 6015.430022] usb 2-1: reset high speed USB device using ehci_hcd and address 14
Nov 16 18:01:53 derek-desktop kernel: [ 6020.702517] usb 2-1: reset high speed USB device using ehci_hcd and address 14
Nov 16 18:01:53 derek-desktop kernel: [ 6021.300015] usb 2-1: reset high speed USB device using ehci_hcd and address 14
Nov 16 18:01:54 derek-desktop kernel: [ 6021.900018] usb 2-1: reset high speed USB device using ehci_hcd and address 14
Nov 16 18:01:54 derek-desktop kernel: [ 6022.442513] usb 2-1: reset high speed USB device using ehci_hcd and address 14
Nov 16 18:01:55 derek-desktop kernel: [ 6022.862035] scsi 14:0:0:0: Device offlined - not ready after error recovery
Nov 16 18:01:55 derek-desktop kernel: [ 6022.862050] usb 2-1: USB disconnect, address 14

Any ideas on what this means?

Also, though it may have been doing it before, I noticed a mild very quiet tapping sound while plugged in.  Note that this isn't the loud clicking of hard drive failure and note also that (as I just verified) the drive does NOT make this sound on a windows system or my laptop (8.04).

Any further help would be greatly appreciated!!!

---

### Post by kirmonkey on 2009-11-16
Hey,

I have an idea.

I have an externel HDD connected to my computer - there are frequent power cuts here - after a power cut the HDD is not spotted/mounted. I open gparted and the disk is spotted. I run "check disk" and re-boot (you could re-mount with a command). The disk is there upon re-boot.

Never had the energy to get to the bottom of the problem.

ALWAYS BACKUP YOUR DATA!

---

### Post by Giblet5 on 2009-11-16
It looks like the USB's hdd interface is erroring out.

I'm sorry, I don't know how to diagnose this, but it seems to be a known problem with USB-connected drives with SMART capability.

See [bug 474988]("https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/474988").

You could try checking to see if the SMART feature can be turned off via a jumper on that disk drive... Otherwise, I got nuthin'.

---

### Post by Bugs318 on 2009-11-16
Just thought I'd fill you in on a rather odd fix:

It seems after many hours of googling help for this problem, someone had said it could be a cable issue, so I tried a different cable.

Oddly enough, it worked fine with a different cable, even though the original cable was sufficient for several other computers... odd, but resolved!

Thanks for your help!

---

### Post by kirmonkey on 2009-11-17
You should be able to mark this thread as [SOLVED] then.

---

### Post by Mach1US on 2009-11-17
At **Bugs318**

```
Can someone help me either figure out how to get the device listed
 in the fdisk -l command (as it does on my laptop) or else another 
way to discern the /dev/sdxx location of the device so I can mount it?
```

```
sudo lshw -C disk
```

---

