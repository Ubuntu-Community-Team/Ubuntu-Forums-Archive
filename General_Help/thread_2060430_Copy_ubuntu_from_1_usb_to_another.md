---
title: "Copy ubuntu from 1 usb to another"
date: 2012-09-20
forum: General Help
---

### Post by MrC11 on 2012-09-20
Hello guys,

I got 1 usb with a fresh installation of ubuntu 12.04 and 1 empty usb.
How can I copy the usb with the installation to the other one which is empty?

I have windows 7 and ubuntu 12.04. In which OS I should copy it?

Greetz

---

### Post by prshah on 2012-09-20
> **MrC11 said:**
> 1 usb with a fresh installation of ubuntu 12.04 and 1 empty usb.
How can I copy the usb with the installation to the other one which is empty?
...
In which OS I should copy it?


Use Ubuntu, live or installed.

In ubuntu (or any linux) use "dd" to clone the usb. IMPORTANT NOTE: "dd" is a very dangerous command if not used with utmost care. A single mispelling will lead to INSTANT data loss. Use at your own risk.

Plug in both your USB drives (one at a time), preferably on different buses. Unmount any mounted partitions (check with applications gparted or palimpsest)

You can give the following command in the Terminal (Applications-Accessories-Terminal / Dash-Terminal)

```
sudo dd if=/dev/sdX of=/dev/sdY bs=64M
``` This will clone your original usb (input file sdX) to your new USB pen drive (output file sdY). Replace sdX and sdY with the device identifiers assigned to your pen drives (use the command "sudo fdisk -l" to find the device identifiers).

If your pendrive sdY is GREATER in size than sdX, then additionally use gparted to resize the partition to full size.

If you find that your USB bus cannot handle both pen drives together (some USB buses do not have enough current to handle multiple USB devices) then you can do this one at a time, as```

#plug in your original pendrive, unmount partitions, then,
#first, create a clone image
sudo dd if=/dev/sdX of=/root/usbstick.img bs=64M
#unplug original when done, plug in new pen drive, unmount partitions, then
sudo dd of=/dev/sdY if=/root/usbstick.img bs=64M
# in this case, sdX and sdY MAY be same.
# delete original clone file
sudo rm /root/usbstick.img

```


Please post back if you have any questions or queries. This information is correct, but presented AT YOUR OWN RISK ONLY, please.

---

