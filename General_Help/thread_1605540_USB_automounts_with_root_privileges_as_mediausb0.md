---
title: "USB automounts with root privileges as /media/usb0?"
date: 2010-10-25
forum: General Help
---

### Post by J-Rod on 2010-10-25
So yeah, not sure if this is a silly issue or what. I recently upgraded to 10.10. When I insert my usb device, it automounts as /media/usb0, with root privileges. I have to manually unmount it, and afterwards if I select the "mount (drivename)" usb stick from Places it will automount as /media/(devicename) with proper permissions. Any ideas?

---

### Post by J-Rod on 2010-10-26
Here's the syslog output after inserting a USB stick:

```
Oct 26 15:15:39 Tiamat kernel: [97766.736081] usb 1-4: new high speed USB device using ehci_hcd and address 11
Oct 26 15:15:39 Tiamat kernel: [97766.888134] scsi8 : usb-storage 1-4:1.0
Oct 26 15:15:40 Tiamat kernel: [97767.893194] scsi 8:0:0:0: Direct-Access     Corsair  Flash Voyager    0.00 PQ: 0 ANSI: 2
Oct 26 15:15:40 Tiamat kernel: [97767.899551] sd 8:0:0:0: Attached scsi generic sg2 type 0
Oct 26 15:15:40 Tiamat kernel: [97767.905045] sd 8:0:0:0: [sdb] 15794176 512-byte logical blocks: (8.08 GB/7.53 GiB)
Oct 26 15:15:40 Tiamat kernel: [97767.905637] sd 8:0:0:0: [sdb] Write Protect is off
Oct 26 15:15:40 Tiamat kernel: [97767.905648] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
Oct 26 15:15:40 Tiamat kernel: [97767.905655] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Oct 26 15:15:40 Tiamat kernel: [97767.909071] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Oct 26 15:15:41 Tiamat kernel: [97767.909094]  sdb: sdb1
Oct 26 15:15:41 Tiamat kernel: [97768.246117] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Oct 26 15:15:41 Tiamat kernel: [97768.246134] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Oct 26 15:15:41 Tiamat usbmount[13032]: /dev/sdb does not contain a filesystem or disklabel
Oct 26 15:15:42 Tiamat usbmount[13060]: executing command: mount -tvfat -osync,noexec,nodev,noatime,nodiratime /dev/sdb1 /media/usb0

```

here's the output of a mount command after the initial insert:

```
/dev/sdb1 on /media/usb0 type vfat (rw,noexec,nodev,sync,noatime,nodiratime)

```

so after that, I can unmount it manually:

sudo umount /dev/sdb1

and then go to "Places" and select the name of the USB Volume from there, and it does another automount, and that one has proper user level privileges for the logged in user.

I'm a bit stumped, so if anyone even has a direction for me to look into I'd greatly appreciate it!

---

### Post by spazzm on 2010-11-19
I had the same problem on 10.10 until I uninstalled the following:

[LIST]
[*]usb creator
[*]usbmount
[*]gnome-pilot
[/LIST]
Now USB automounts correctly.

---

### Post by aleixsr on 2011-11-04
Same solution here,
thanks.

---

