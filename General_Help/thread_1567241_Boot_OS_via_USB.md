---
title: "Boot OS via USB"
date: 2010-09-03
forum: General Help
---

### Post by WiReIs on 2010-09-03
Hello, im having a little problem booting up an OS via USB..

im running Ubuntu 10.04 (installed OS) and i wish to boot up a live 

version of Backtrack4 via my 16gb Verbatim USB flash

ive tried going through the boot selection menu (F12) and selecting 

USB flashdrive, and also into "setup" and giving the USB priority  

but it doesnt seem to boot up just a blank screen 

with a flashing cursor top left of screen.

The file i have saved on my USBflash is an .iso file

any help very much appreciated :D

---

### Post by Nytram on 2010-09-03
> **WiReIs said:**
> The file i have saved on my USBflash is an .iso file


You need to burn an image of the .iso file, not the file itself. From Ubuntu, right click on the .iso file and there should be an option to "Write image to disk" or similar. (I'm not in Ubuntu right now, so don't recall the exact wording.)

---

### Post by WiReIs on 2010-09-03
> **Nytram said:**
> You need to burn an image of the .iso file, not the file itself. From Ubuntu, right click on the .iso file and there should be an option to "Write image to disk" or similar. (I'm not in Ubuntu right now, so don't recall the exact wording.)

Thanks for your help :D thats it

---

### Post by oldfred on 2010-09-03
You can directly boot an ISO with grub2's loopmount. I have several ISOs that I boot that way. Not sure if backtrack supports the loops mount as I think it is based on older Ubuntu that did not.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

This script has a way to boot backtrack
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by C.S.Cameron on 2010-09-03
FYI sundar_ima claims Backtrack iso can be booted using grub2, see:
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

