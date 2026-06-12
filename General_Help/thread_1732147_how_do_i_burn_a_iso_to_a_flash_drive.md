---
title: "how do i burn a iso to a flash drive?"
date: 2011-04-17
forum: General Help
---

### Post by cbennett a7xftw on 2011-04-17
well the title says it all..

---

### Post by wojox on 2011-04-17
If it's an Ubuntu.iso use the StartUP Disk Creator. There's Unetbootin if you want a graphical app or else dd the sucker.

---

### Post by cbennett a7xftw on 2011-04-17
> **wojox said:**
> If it's an Ubuntu.iso use the StartUP Disk Creator. There's Unetbootin if you want a graphical app or else dd the sucker.

dd? i have no clue what that means..

---

### Post by garvinrick4 on 2011-04-17
Do you want to create a Live CD and installer in the usb flash or do you want to install a operating system with partitions like on a hard disk?

---

### Post by wojox on 2011-04-17
> **cbennett a7xftw said:**
> dd? i have no clue what that means..

It's a program already installed for copying stuff. Command line. Your probably better of with one of the first two options.

---

### Post by cbennett a7xftw on 2011-04-17
> **garvinrick4 said:**
> Do you want to create a Live CD and installer in the usb flash or do you want to install a operating system with partitions like on a hard disk?

umm i want to use it to put windows 7 on my friends computer... no partitioning needed i dont want a live cd or anything

---

### Post by WorMzy on 2011-04-17
There's a couple of suggestions on here: [http://serverfault.com/questions/6714/how-to-make-a-windows-7-usb-flash-install-media-from-linux](http://serverfault.com/questions/6714/how-to-make-a-windows-7-usb-flash-install-media-from-linux)

Make sure you use the right device identifier for your USB stick though. e.g. if you have three harddrives in your PC, your flash drive (when inserted) will probably be sdd. Use ```
sudo fdisk -l
``` to check if you're not sure.

---

### Post by cbennett a7xftw on 2011-04-17
> **WorMzy said:**
> There's a couple of suggestions on here: [http://serverfault.com/questions/6714/how-to-make-a-windows-7-usb-flash-install-media-from-linux](http://serverfault.com/questions/6714/how-to-make-a-windows-7-usb-flash-install-media-from-linux)

Make sure you use the right device identifier for your USB stick though. e.g. if you have three harddrives in your PC, your flash drive (when inserted) will probably be sdd. Use ```
sudo fdisk -l
``` to check if you're not sure.

well...

---

### Post by racie on 2011-04-17
> **cbennett a7xftw said:**
> umm i want to use it to put windows 7 on my friends computer... no partitioning needed i dont want a live cd or anything
There's actually a tool specifically made for installing Windows 7 through USB [here](http://wudt.codeplex.com/).

---

### Post by cbennett a7xftw on 2011-04-17
> **racie said:**
> There's actually a tool specifically made for installing Windows 7 through USB [here](http://wudt.codeplex.com/).

hmm this would be great i hope it works

and it dosnt :(

---

### Post by racie on 2011-04-18
> **cbennett a7xftw said:**
> hmm this would be great i hope it works

and it dosnt :(

What exactly didn't work about it?  I've used it on my laptop before and everything worked fine.

Remember to change the boot order in the BIOS so that the USB will boot first.

---

### Post by thecamelcoder on 2011-04-18
Hey mate, take a look at these two links and see if they don't solve your situation. 

The first is how to build a bootable image
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)

and this one is how to actually boot from that drive
[http://www.linux-geek.co.nz/2011/04/11/how-to-boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](http://www.linux-geek.co.nz/2011/04/11/how-to-boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)

Let me know how you get on. 
):P

---

### Post by WorMzy on 2011-04-18
> **cbennett a7xftw said:**
> well...

Well what? :confused:

---

### Post by C.S.Cameron on 2011-04-19
To make a Windows 7 install disk, format it NTFS using gparted and set the boot flag.
Copy the stuff inside the Windows 7 iso to the drive or copy the files off of the Windows DVD.

---

