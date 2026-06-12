---
title: "installing netbook remix from flash"
date: 2010-01-12
forum: General Help
---

### Post by liverpool4life on 2010-01-12
hey, 

much respect and thanks if you can help me out with this one-- i was in the process of trying to put the latest version of netbook remix on a flash drive (2gb Kingston), but failed mid-process. I had forgotten to format to FAT32, and thus ran into problems in the middle. I'm now left with a flash drive that is partially written to, and completely write-protected. And I can't get rid of anything on the flash drive. Nothing I've tried (Killdisk, re-formatting, MS-DOS) has helped me erase the flash drive permanently (every time I try Windows returns the message that the device is write-protected). Neither can I re-run the USB installer, which I downloaded from the pendrivelinux folk. 

Can anyone help me? Either in erasing my flash drive completely, and starting again -- or in re-doing the making of this flashdrive into a boot disk for the netbook remix version of ubuntu. 

thanks all!

---

### Post by spiderbatdad on 2010-01-12
I think ```
chattr -i <dev>
``` might help you. See man chattr for more info. The above command where <dev> is /dev/sdb or whatever is your flash device...**BE VERY CERTAIN** of the device before you run the command.  Run mount or sudo fdisk -l and locate the device to be sure.

---

### Post by warfacegod on 2010-01-12
It sounds like you are trying to do this from Windows. You will probably get better results from a linux machine if you have one available or an install disc you can run a liveCD environment from.

---

### Post by spiderbatdad on 2010-01-12
meh I don't think the above will run. Instead cd into the device and run chattr -i file to remove write protection on file. Where file is substituted with actual file name.

---

