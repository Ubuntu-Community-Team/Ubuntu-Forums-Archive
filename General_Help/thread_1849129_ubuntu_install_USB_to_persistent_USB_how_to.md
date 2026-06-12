---
title: "ubuntu install USB to persistent USB how to?"
date: 2011-09-23
forum: General Help
---

### Post by ipatch on 2011-09-23
I'll try my best to make this short.  Basically my computer is in a super fragile state right now, and I am trying to get some stability.  So this is where I am at.  I downloaded the 11.04 ISO and created a bootable USB using Unetbin in Windows.  I couldn't get any graphics on my display until issuing the following command by hitting the "Tab" key during boot up.

```
i915.modset=1
```After putting that at the end of the string of parameters I am able to get video on the screen.  I installed Ubuntu to the internal hard drive on the laptop, and tried to boot the stock kernel using the stock version of grub, but all I get is a blank screen, so I am stuck with the USB for the time being.  I would like to find a way to make the USB persistent, so I don't have to keep adjusting the settings every time I boot it up, but all I could find was this: 

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

and unfortunately when I try to create the ```
casper-rw
``` file on the / "root" of the usb, I am getting a read only file-system, now I know theres got to be an easy way to make this drive pesistent.  Any help would be greatly appreciated.

---

### Post by mmsmc on 2011-09-23
you could re-install it on the usb drive and set the persistence with the universal usb installer [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

