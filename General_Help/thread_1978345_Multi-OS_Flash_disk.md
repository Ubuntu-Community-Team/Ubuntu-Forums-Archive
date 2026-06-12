---
title: "Multi-OS Flash disk"
date: 2012-05-11
forum: General Help
---

### Post by astrobob.tk on 2012-05-11
Hello,

:D as the title suggests, I am interested in configuring a flash disk to be able to boot several OS's

I found about his but haven't read it all yet:
[http://www.boards.ie/vbulletin/showthread.php?t=2055556407](http://www.boards.ie/vbulletin/showthread.php?t=2055556407)

I am thinking of 4 OS's + a data directory (encrypted!)

I am writing to get you're feedback on this & read any of your suggestions.

Thanks in advance

---

### Post by Megaptera on 2012-05-11
That looks like quite an old article.
Have you looked at this "How To Boot 10 Different Live CDs From 1 USB Flash Drive" from here [http://www.howtogeek.com/howto/39747/how-to-boot-10-different-live-cds-from-1-usb-flash-drive/](http://www.howtogeek.com/howto/39747/how-to-boot-10-different-live-cds-from-1-usb-flash-drive/) which is more recent.

---

### Post by oldfred on 2012-05-11
I did it manually with grub2 and its loopmount before the scripts were available. Different scripts use different boot loaders.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

How large is flash drive? I have a 4GB with just 5 or 6 ISOs as some are smaller. I also have a full install in a 8GB / partition but also boot serveral ISO from my 8GB data partition on a 16GB flash.

Not sure if grub2 can boot an ISO from an encrypted partition, but you can do the full install.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

I think one of these is the same as the link in Megaptera post that reviews the process.

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub4dos
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)

---

### Post by astrobob.tk on 2012-05-13
Thank you both for your replies.

It seems that what you both suggest are "Live" OS's. I was looking for something more "persistent" like the option that Knoppix offers?

P.S.: I am aiming for persistent installations on a 32GB flash disk (to get)!

thanks again

---

### Post by oldfred on 2012-05-13
If you have a 32GB flash, you really do not want persistent, but just a full install.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

An install to a flash drive is just like any install to a second drive except you make some settings to reduce writes as that is where flash is very slow.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

I have a 16GB flash with a full install  in the first 8GB and data in the rest of the flash drive. In the data area I also have several ISO to make it a multi-OS boot also. Those are more for repairs since flash stick is easy to carry around.

While I did a full install to also allow me to test it on my laptop which does not have a lot of room for another install, you may want a lighter weight version as it may work better especially if system is not high powered. RAM becomes the important issue as Ubuntu caches what you do, so if you have a lot of RAM the slowness of flash & the USB connection become less noticeable.

Installs to 4GB flash, newer versions of Ubuntu require 4.4GB as minimum
HOW TO Avoid Wubi & Install Ubuntu 10.04 on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

---

### Post by astrobob.tk on 2012-09-06
Thanks all for the links.

I haven't really started with preparing my usb; I'm still brainstorming.

Here's a related post: [http://megaman86.dyndns.org/?p=130](http://megaman86.dyndns.org/?p=130) (MultiSystem; different from MultiSystem in post 3?)

---

### Post by lykwydchykyn on 2012-09-06
I highly recommend multisystem.  Been using it for years, I have oodles of distros booting from my 32Gb flash drive.  Plus I can boot the Windows XP installer/repair console for situations where I need to repair an XP machine.

Updating or adding new distros is just drag&drop.  Best solution I've ever used for USB booting (and I've used quite a few over the years...).

---

