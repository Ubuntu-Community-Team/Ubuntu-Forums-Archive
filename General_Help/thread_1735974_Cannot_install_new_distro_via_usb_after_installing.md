---
title: "Cannot install new distro via usb after installing Crunchbang"
date: 2011-04-22
forum: General Help
---

### Post by trstncmpbll on 2011-04-22
I love to distro hop and I am always installing new linux distros via usb. After installing the latest Crunchbang distro I tried swithing to a few different other linux distros and every time I try to boot them I get a black screen with a blinking _

I have tried 3 different usb drives and my cards are formatted to FAT32, I have tried using unetbootin and pendrivelinux,

Its always the same black screen so it has to be something irrelevant to the distro and usb drive

Thank you all for any help

---

### Post by snowpine on 2011-04-23
Have you tested the USB drive on another computer?
Have you tried using a Live CD?
Have you tried using the distro's own USB creation software (for example Ubuntu's 'usb-creator-gtk' or Fedora's 'liveusb-creator') rather than a 3rd-party app like Unetbootin?

To answer your question, booting from USB is a function of your BIOS and happens before the OS on your hard drive is loaded. Therefore it should not matter whether you have CrunchBang (or any other distro) installed. I think it's a coincidence. :)

---

### Post by oldfred on 2011-04-23
Not for your current problem but something to consider.

If you like to distro hop, it may be easier just to install multiple ISOs on one USB flash drive & loop mount boot them.

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

I did it manually before finding above scripts:
ISO Booting with Grub 2 - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
HOWTO: Boot & Install Ubuntu ISO from the Grub Rescue Prompt
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

---

