---
title: "Use ubuntu from usb device"
date: 2012-05-16
forum: General Help
---

### Post by Rinilmg on 2012-05-16
My internal HDD crashed and i have sent it for the servicing. can i now use ubuntu from a external usb device (ie without internal HDD. )

---

### Post by 2F4U on 2012-05-16
Yes, you can. You have two options, with and without persistent area. Without persistent area the usb behaves like a liveCD, i.e. you are not allowed to make any changes.

---

### Post by loklaan on 2012-05-16
If you have a thumb-drive and the means to turn it into a [bootable drive]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") then you can run Ubuntu off of it. When making the thumb-drive, be sure to set a reasonable storage space.

edit: The storage space is referred to as the *persistent area*, as 2F4U mentioned above.

---

### Post by codemaniac on 2012-05-16
Yes surely you can .Here is a resource for you .
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by et_tu_brute on 2012-05-16
> **Rinilmg said:**
> My internal HDD crashed and i have sent it for the servicing. can i now use ubuntu from a external usb device (ie without internal HDD. )
I am doing what you seek now. Currently using a decdicated 8gb Lexar USB drive with the persistent option. It is a little slower than the Live CD, but at least the changes that are made are stored. In addition, I have synced files created with the Ubuntu One "cloud" for extra safety.
I have a new hdd coming for my pc, so I can continue on in the meantime. There are instructions on the Ubuntu website providing simple and accurate instructions on how to download the ISO image and to "burn" the ISO image to a thumb drive. It was all very simple, as long as you remember to select the "persistant" option when it comes up.
The beauty of having Ubuntu on the USB drive meant that I could run 'gparted' and analyse my failed hdd to see where the problem lay before I wasted hours trying to get the hdd tgo work again. :)

---

### Post by wilee-nilee on 2012-05-16
> **et_tu_brute said:**
> I am doing what you seek now. Currently using a decdicated 8gb Lexar USB drive with the persistent option. It is a little slower than the Live CD, but at least the changes that are made are stored. In addition, I have synced files created with the Ubuntu One "cloud" for extra safety.
I have a new hdd coming for my pc, so I can continue on in the meantime. There are instructions on the Ubuntu website providing simple and accurate instructions on how to download the ISO image and to "burn" the ISO image to a thumb drive. It was all very simple, as long as you remember to select the "persistant" option when it comes up.
The beauty of having Ubuntu on the USB drive meant that I could run 'gparted' and analyse my failed hdd to see where the problem lay before I wasted hours trying to get the hdd tgo work again. :)

Sooner or later you will fill up that persistent file and it is not really cleanable, and it will be bricked if not bootable until you remove the persistent file, with that size a thumb I would do a full install on it.

---

### Post by TRG1 on 2012-06-07
I've made a couple of attempts to create a Linux Live bootable thumb drive using a SanDisk 8gb drive. First I formatted the drive. Then I tried these two ways:
1)Linux Live USB Creator 2.8.12
2)unetbootin-windows-575

I was trying to install ubuntu-12.04-desktop-amd64.iso.

I neither case was I able to get my computer to boot from the thumb drive. I know it boots from a thumb drive because I've done it with a version of a Windows 7 installation disk.

Thanks for any assistance you may be able to offer. I want to use the thumb drive to be able to scan the system drive for viruses, among other things.

Nevermind. I think I have found my problem.

---

