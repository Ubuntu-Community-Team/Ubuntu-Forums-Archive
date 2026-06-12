---
title: "usb drive not mounting"
date: 2009-12-14
forum: General Help
---

### Post by eival on 2009-12-14
ive been using this drive for a while and now when i plug it into my laptop it doesnt respond.

it still responds to my xbox 360 which is what i last had it plugged into.

any ideas?:popcorn:

---

### Post by jbrown96 on 2009-12-14
Does it appear in "Places"?

If that still doesn't work, could you post the output of the following commands:

Run this command before and after you plug it in, and post the output here. ```
sudo fdisk -l
```

---

### Post by kitten16 on 2009-12-14
Did you do anything to your laptop beforehand (upgrade, update, installed, edited a system file)?  

Maybe this isn't anything helpful, but when I upgraded from Dapper to Hardy, I couldn't mount my USB devices at first, but when I restarted the computer, everything worked fine.

---

### Post by eival on 2009-12-14
> **jbrown96 said:**
> Does it appear in "Places"?

If that still doesn't work, could you post the output of the following commands:

Run this command before and after you plug it in, and post the output here. ```
sudo fdisk -l
```

theres a LED light that normally blinks when i plug it in, an it doesnt even blink anymore when i plug it into laptop, it does when i plug it into my 360.

as for the output

```
cus@cus-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaab3dcbc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       19457   105089197+   5  Extended
/dev/sda5            6375       18920   100775713+  83  Linux
/dev/sda6           18921       19457     4313421   82  Linux swap / Solaris

```


> **kitten16 said:**
> Did you do anything to your laptop beforehand (upgrade, update, installed, edited a system file)?  


there was a system update over the weekend that forced me to restart for the changes to take effect, during that time i hadnt reattached the usb to my laptop, so perhaps that has something to do with it. i dont remember what the updates were for tho.

and id rather not restart again cause im having another issue thats causing ubuntu to boot into "low graphics mode" rather than using the latest nvidia driver ive installed, but ive already created a topic about that issue, hoping to get it fixed.

---

### Post by llamabr on 2009-12-14
Often, when windows hasn't quite finished doing whatever it was doing, the filesystem will be corrupted.  When you remove from windows, you need to click that little "safely remove device" button.  I don't know how it works on an xbox.

Anyway, plug it in, hang back 15 seconds, and then post:

```
dmesg | tail
```

---

### Post by eival on 2009-12-14
> **llamabr said:**
> 
Anyway, plug it in, hang back 15 seconds, and then post:

```
dmesg | tail
```

```
cus@cus-laptop:~$ dmesg | tail
[72819.118016] usb 1-1: configuration #1 chosen from 1 choice
[72819.127300] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:0b.0/usb1/1-1/1-1:1.0/input/input13
[72819.156101] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:0b.0-1
[72822.135734] usb 1-1: USB disconnect, address 5
[72830.616576] usb 1-6: new low speed USB device using ohci_hcd and address 6
[72830.798819] usb 1-6: configuration #1 chosen from 1 choice
[72830.807812] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:0b.0/usb1/1-6/1-6:1.0/input/input14
[72830.829809] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:0b.0-6
[72856.920581] usb 2-1: new high speed USB device using ehci_hcd and address 21
[72857.040809] usb 2-1: configuration #1 chosen from 1 choice
cus@cus-laptop:~$ 

```

---

### Post by llamabr on 2009-12-14
Weird.  Maybe we should also see 

```
lspci
```

In the meantime, try:

```
sudo modprobe -r ohci_hcd
```

and plug it in again, and then (this time wait more like 30 seconds):

```
dmesg | tail
```

---

