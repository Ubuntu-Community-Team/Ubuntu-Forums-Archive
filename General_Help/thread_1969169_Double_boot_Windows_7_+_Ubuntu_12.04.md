---
title: "Double boot Windows 7 + Ubuntu 12.04"
date: 2012-04-29
forum: General Help
---

### Post by pakoelchako on 2012-04-29
[SIZE=3]Hi guys.
 I recently erased my hard drive and installed Windows 7, leaving about 100 GB to install Ubuntu. After installing both OS's correctly, whenever I sart my laptop, Windows 7 automatically boots and I can't boot Ubuntu. The oly way y can boot it is with my flash drive inserted into the usb port. I tried to fix this with easybcd and didn't get it. 


My system specs:
AMD athlon x2
2GB RAM
320 GB HD
HP Pavillion dv4[/SIZE]

---

### Post by Zukaro on 2012-04-29
It sounds like grub got installed to the USB and not the hard drive.  Try opening a terminal and typing "sudo update-grub"; I've heard that works.  If that doesn't work then boot into Ubuntu and remove the USB once you're in Ubuntu; then type "sudo update-grub", I don't know if that would make a difference.

---

### Post by Alan.Brown on 2012-04-29
It sounds like you have installed Ubuntu first then Windows - if there is a next time, install Windows first.

Boot Ubuntu from your from your Flash Drive.   

Open a Terminal and enter the following -
```

[B]mkdir mnt
sudo mount /dev/sda? /mnt
sudo grub-install --root-directory=/mnt /dev/sda[/B]
```This assumes that your Hard Drive is **sda**. 

The first line creates a mount point at **/mnt**.

The second line mounts your Ubuntu partition to the mount point.   **sda?** is the partition number where you have Ubuntu installed (eg **sda2**, **sda3, **etc).

The third line installs the MBR onto your Hard Disk boot sector (**/dev/sda**) using the root of your Ubuntu installation.

Reboot and go into Ubuntu.   To be sure I usually enter the two following commands from within Ubuntu -
```

[B]sudo update-grub
sudo grub-install /dev/sda[/B]
```Again assuming that your Hard Disk to boot from is **sda**.

When you reboot, Ubuntu should be your default OS and you can choose Windows from the Boot menu.

Hope this helps

Alan.

---

### Post by pakoelchako on 2012-04-30
Thanks a lot, both answers were pretty useful and I can now boot without the flash drive.

---

