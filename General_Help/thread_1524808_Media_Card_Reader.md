---
title: "Media Card Reader"
date: 2010-07-05
forum: General Help
---

### Post by Joker34563 on 2010-07-05
I have a not so great acer aspire with ubuntu installed on it. I have a media card reader on the tower, however, it doesnt seem to be working. I put the card in, a green light comes on, but I can't find any of the files.

Can someone help me out? Is there a drive i need to install?

---

### Post by btindie on 2010-07-05
To see if it detects it correctly type
```
sudo dmesg | tail
```
after inserting the card wait a few seconds before issuing the command. It should say something about finding a new drive/partition, e.g. /dev/sdf. You can then mount it. Include the output of the above command if you need further help.

---

### Post by SoFl W on 2010-07-05
> **Joker34563 said:**
> I have a not so great acer aspire with ubuntu installed on it. I have a media card reader on the tower, however, it doesnt seem to be working. I put the card in, a green light comes on, but I can't find any of the files.

Can someone help me out? Is there a drive i need to install?

Did it work at one time?
I have a older card reader that wont read any newer cards.

---

### Post by Joker34563 on 2010-07-05
where do i enter the code?

---

### Post by Joker34563 on 2010-07-05
[257629.700089] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 336
[257749.702146] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 253
[257869.704416] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 252
[257989.705279] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 336
[258109.701736] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 336
[258229.700206] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 337
[258349.708088] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 253
[258469.698829] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 337
[258589.708060] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 253
[258709.701347] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 337

---

### Post by btindie on 2010-07-05
In to the terminal
 
Try just
```
sudo dmesg
```
about 10 seconds after you've inserted the card then scroll up and you're looking for something that mentions '/dev/sd?'

---

### Post by Joker34563 on 2010-07-05
255506.176039] usb 2-8: reset full speed USB device using ohci_hcd and address 3
[255516.556038] usb 2-8: reset full speed USB device using ohci_hcd and address 3
[255532.944033] usb 2-8: reset full speed USB device using ohci_hcd and address 3
[255533.328036] usb 2-8: reset full speed USB device using ohci_hcd and address 3
[255543.716029] usb 2-8: reset full speed USB device using ohci_hcd and address 3
[255543.923046] sd 4:0:0:0: Device offlined - not ready after error recovery

---

### Post by btindie on 2010-07-05
Does it report anything else?
 
With the card removed type
```
ls /dev/sd*
```
then insert the card and give it a while to settle and type the above again. Are there any new entries? If there are then this is your card and you can just mount it.

---

### Post by Joker34563 on 2010-07-05
nothing new

---

### Post by Joker34563 on 2010-07-06
Any other ideas on how to get this to work?

---

### Post by dabl on 2010-07-06
With the card in the slot, in a terminal window do ```
lsusb
``` and post the output.

---

### Post by Joker34563 on 2010-07-06
Bus 001 Device 003: ID 045e:0728 Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by btindie on 2010-07-06
It's a know bug, take a look at
[https://bugs.launchpad.net/ubuntu/+bug/366478](https://bugs.launchpad.net/ubuntu/+bug/366478)
[http://ubuntuforums.org/showthread.php?t=1136196](http://ubuntuforums.org/showthread.php?t=1136196)
 
There's one possible solution mentioned but it may not work.
 
I found them by googling for **Linux Alcor Micro Corp. 8-in-1 Media Card Reader**. Use Google, it's there to help!

---

