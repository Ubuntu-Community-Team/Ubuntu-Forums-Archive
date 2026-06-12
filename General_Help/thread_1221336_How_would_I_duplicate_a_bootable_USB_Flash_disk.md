---
title: "How would I duplicate a bootable USB Flash disk?"
date: 2009-07-23
forum: General Help
---

### Post by RickSimnett on 2009-07-23
Hello,
I have a bootable usb flash disk, which is setup exactly as I need it with ubuntu 9, and various srver softwares. What I want to do is to be able to make exact copies of this flash disk to identical flash drives, so that I can skip reinstalling and reloading software on a small deployment of ATOM servers. Can anyone tell me how to make bootable duplicates of my flash drive?

Thanks,
Rick

---

### Post by Rocket2DMn on 2009-07-23
You want to use the dd command for that.  You can make an image of your current disk so you don't have to copy it every time (where sdb is the flash device):
```
dd if=/dev/sdb of=/path/to/file.img
```
Then to load the image to another device (like another flash drive).  I believe you need sudo for this one - run
```
sudo dd if=/path/to/file.img of=/dev/sdb
```

There is also a graphical program called usb-imagewriter which can be used to write img files to a device.

---

