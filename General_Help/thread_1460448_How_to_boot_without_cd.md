---
title: "How to boot without cd??"
date: 2010-04-22
forum: General Help
---

### Post by Vasichko on 2010-04-22
Never tried Ubuntu before and never had an issue when I ran Red Hat back in the day.

How do I get my pc to boot without me using the cd???

I installed the boot loader on hd0 which shouldnt be and issue???

---

### Post by spcwingo on 2010-04-22
You could also use unetbootin to create a bootable USB flash drive.

[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

---

### Post by themusicalduck on 2010-04-22
Which version of Ubuntu are you using?

Did you install it off the CD onto a new partition? You say you installed the bootloader.. but there's not much use just installing the bootloader and not the OS.

Generally if you click Install on the desktop when you have booted in using the CD it will take you step by step through installing it.

---

### Post by drs305 on 2010-04-22
Which bootloader? Grub2 can boot an Ubuntu LiveCD iso if you have the iso file on your disk but you haven't given us enough information yet to really help you. 

Although I suspect it unlikely, if you happen to have Grub 2 installed and an Ubuntu iso, give us the iso name, partition and path and we can build a menuentry for you.

Edit: Do you just mean you want to run the OS without using the CD? If you have the CD, from the Desktop, which is probably where you are if you chose "Try Ubuntu without Installing", just install Ubuntu by clicking on the "Install" icon once the CD boots.

---

### Post by wilee-nilee on 2010-04-22
Go virtual.

---

### Post by The Thunder Chimp on 2010-04-22
You can install it via a CD or you can boot from a USB (see [http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)) and then install it from the booted device.

---

### Post by Vasichko on 2010-04-22
OS is already installed.  

Everytime I power down and power back up it asks for a device to boot from or tells me to insert a CD and hit enter.

I can not boot to the OS without having the cd in for some reason.  

When installing I checked the box that said install boot loader and it was installed to hd0.

Im installing the latest 64bit ubuntu.

---

### Post by themusicalduck on 2010-04-22
Does this error come up when grub loads or does it appear to be an error message that appears when the BIOS is loading?

It might be that you need to set your BIOS to boot from the hard drive. If you set it to boot the CD on startup when you installed Ubuntu, you need to set it back to how it was to boot from the hard drive again.

Usually it tells you how to get into "Setup" or something like that when the computer first turns on. On my PC you have to press delete, but it might be a function button. You need to find the boot order and set it to hard drive, (or it might hdd or something like that).

If it comes up in grub and you can't boot unless the Ubuntu CD is in then that sounds a bit strange and I'm not sure what to suggest.

---

### Post by Vasichko on 2010-04-22
My bios wasnt set to my harddrive.  Guess I might have changed it on accident earlier???  Oh well all is well now.

---

