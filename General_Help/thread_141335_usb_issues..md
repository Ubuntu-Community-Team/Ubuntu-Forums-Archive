---
title: "usb issues."
date: 2006-03-08
forum: General Help
---

### Post by dmizer on 2006-03-08
first of all, my thanks to the powers that be for creating a linux os which installed with nearly full support on the first go of a particularly cranky japanese oem nec versapro va90j laptop.  tried slackware, debian, and fedora core ... none of which would install correctly.

anyway, on to my problem.  my usb doesn't work.  i believe it's because there's something physically wrong with it, but i'm not sure.

on boot i get the following:
uhci_hcd host system error, pci problems.
uhci_hcd host controller halted.

per the wiki, i tried rmmod echi_hcd, but only got: module echi_hcd does not exist in /proc/modules.  i assumed that was because of the above said errors during boot.

so i tried modprobe echi_hcd but the module wasn't found.  and none was listed when i did a -l switch.

i would attempt to create an unusual device entry, but the results of lsusb only give me 0000:0000 for the id.

so, in case the integrated usb module in my laptop may or may not be good, i tried a pcmcia card usb 2.0 adapter, which is listed in the device manager as a via technologies inc vt82xxx usb 2.0.

but when i plug my buffalo ruf2-s flash drive into the usb slot, it is not found, and i can't get it to come up by mounting it, and it's not listed in the /mnt directory, and fproc doesn't have a listing for the device either.

not too sure where to go on this one.  i've done quite a bit of research, and i haven't quite stumbled on the answer i need yet.  hope you can help.

---

### Post by dmizer on 2006-03-14
okay ... solved most of my problem on my own here.

1) i had a bad hdd which wasn't allowing dma to work correctly, and was giving me a host of errors all over the place.  replacing the drive fixed the host systems error i was getting.

2) i have a usb 1.0 port, so the ehci module didn't fix my problem.

unloading the uhci module and readding it made my usb flash drive pop right up.

oddly enough ... unloading and reloading the uhci module also made my integrated nic pop up.

any ideas why unloading and reloadingthe uhci module maded everything work?

---

