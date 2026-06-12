---
title: "USB boot and mass storage device"
date: 2011-10-09
forum: General Help
---

### Post by renegadeandy on 2011-10-09
Hiya,

I have a 8GB flash drive - i want to make it a bootable USB drive into linux - but I also want to be able to have a normal flash drive plugging it into any random pc drag and dropping files onto it.

Is there a guide for this - or any best practice? Help!:popcorn:

---

### Post by spiky001 on 2011-10-09
You could create 2 partitions on the usb 1st for install of ubuntu and the 2nd for storage will this help

---

### Post by pr3zident on 2011-10-09
> **renegadeandy said:**
> Hiya,

I have a 8GB flash drive - i want to make it a bootable USB drive into linux - but I also want to be able to have a normal flash drive plugging it into any random pc drag and dropping files onto it.

Is there a guide for this - or any best practice? Help!:popcorn:

use the diskutility

---

### Post by renegadeandy on 2011-10-09
2 partitions sounds like a good idea - I presume the diskutility will help me perform this and the install of the ISO?

---

### Post by spiky001 on 2011-10-09
It should o then format 2nd partition to what you need ntfs if going to used for windows, Maybe you can symlink it to your home in the install  [http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)  Maybe use Gparted to partition usb

---

### Post by renegadeandy on 2011-10-09
So if i install documents / software on the flash drive, power it down, then power it backup again - will the software / documents still exist?

---

### Post by spiky001 on 2011-10-09
If you install them in the 2nd partition they should not the home dir in the ubuntu partition. Basically you have devided the drive into 2 drives

---

### Post by renegadeandy on 2011-10-09
What about software though..if i did apt-get install libreoffice on the flash booted version...where does that get stored - will the installation remain for next boot?

---

### Post by spiky001 on 2011-10-09
You have to make the usb persistant

---

### Post by spiky001 on 2011-10-09
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/)

---

### Post by renegadeandy on 2011-10-09
so how do i make it persistent?:P

---

### Post by spiky001 on 2011-10-09
I put a link in my last post

---

### Post by renegadeandy on 2011-10-09
hmmm, so which option is persistent? The "Stored in extra reserved space" option?

---

### Post by spiky001 on 2011-10-09
Thats what it says

---

### Post by renegadeandy on 2011-10-09
Having installed this, on boot it says vega***.c32 is not a valid boot image , or something similar , then sits on a boot prompt,

waiting for a while it flashes onto the loading screen, followed by a crazy graphical effect - looks like its picking the wrong driver for display - any way I can change that via editting a file whilst booted into normal ubuntu?

---

### Post by renegadeandy on 2011-10-12
Does anybody know how I can fix this? I need it to boot using either standard generic video drivers or ati drivers - and I dont think it is doing that at the moment!

---

