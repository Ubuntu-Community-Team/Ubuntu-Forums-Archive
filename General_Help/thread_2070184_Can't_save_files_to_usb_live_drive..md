---
title: "Can't save files to usb live drive."
date: 2012-10-12
forum: General Help
---

### Post by vanzan on 2012-10-12
I installed Ubuntu 12.04 along with a few other Linux distros to a 64GB usb drive with a Windows program called "YUMI". I love Ubuntu and it's my favorite. The only problem I'm having is that when I download something I can't save it to the USB drive.

I mounted the USB drive and was able to create files from the terminal by using the sudo command. However I was still unable to save files to it using the GUI.

Can anyone please advise me? I was trying for ages using the chmod command and still got nowhere. I'm thinking now that it just may not be possible. I thank you for any help guys! :)

---

### Post by jingaling on 2012-10-12
Hi Vanzan,

This is widely documented in a number of places and a quick google search "how to save files on an ubuntu live USB" will reveal a lot of results I'm sure.

Anyway, the tool your looking for is call "persistence" I'm not sure if Yumi supports it as I haven't used Yumi for a few months. It's basically an extra partition that persistently stores data from within live session throughout reboots. Hence the name. :)

This is done during the 'installation' of the distro to the USB pen though. So you would have to re-create it in order to get persistence. Another option would be to create another partition on your USB pen and store you documents etc on this partition. This wouldn't keep applications and system changes that get made though.

Hope this helps.

---

### Post by vanzan on 2012-10-12
Thank you for taking the time to reply. The funny thing is I am already using peristence mate. YUMI does support it and its homepage gave a link to [this]("http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/") program which I used. I created a 1GB casper-rw file thinking it was enough for small changes. I thought I would be able to save larger files to the root of the usb drive. So if you're are correct it seems I'll have to create a larger casper-rw file! Thank you again.

---

### Post by oldfred on 2012-10-12
It is my understanding that you can only use persistence with one install. With 64GB you could do several full installs.

I have several flash drives. My smaller ones 4GB or less I manually do what you did with yumi. The scripts to add multiple ISO to one flash drive had not be created yet and someone posted info on installing grub2 and using its loopmount to boot ISOs.

But with my larger 16GB flash I did a full install in a 8GB partition and used the other 8GB as data. Part of the 8GB data has several other ISO and I add the loopmount entries to 40_custom. Then the full install is just like any full install, just not generous on space. You do have to change some settings to reduce writes or it will be slow.

My system sees flash drives as another hard drive, so this procedure works for my type of system. 

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

