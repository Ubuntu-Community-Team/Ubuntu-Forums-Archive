---
title: "Cannot edit Grub menu.lst in 10.04??"
date: 2010-05-08
forum: General Help
---

### Post by Satans_Hell on 2010-05-08
Hi guys, I am newish to linux. I am trying out the new Ubuntu 10.04, but when I try to edit the menu.lst for Grub it just comes up with a blank text page??

I am putting in "sudo gedit /boot/grub/menu.lst" but a blank page appears. 

Am I doing it right? 

All I want to do is remove a couple of rogue entries from the menu, but I cant seem to get the menu.lst to appear....

---

### Post by howefield on 2010-05-08
There is no menu.lst in 9.10 onwards.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Satans_Hell on 2010-05-08
> **howefield said:**
> There is no menu.lst in 9.10 onwards.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Thanks for your quick response.

Shame you cant edit the boot list now then, makes it a tad more difficult to remove rogue entries!

Will have to remove grub and use another loader then....

---

### Post by oldfred on 2010-05-08
Actually grub 2 has a lot more capabilities at the expense of some complexity.

General info:
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
drs305's hack to get hidden timeout to work:
[http://ubuntuforums.org/showthread.php?t=1319672](http://ubuntuforums.org/showthread.php?t=1319672)

Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

or:

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

---

### Post by Henery on 2010-05-08
hmm that worked for me in 10.04 sudo gedit /boot/grub/menu.lst
I don't think it is the kernal version but the grub version

---

### Post by oldfred on 2010-05-08
Upgrades keep your old grub legacy as it is not straight forward to convert all the special entries users have added. Upgrades also kept ext3. 

New installs use grub2 and default to ext4 but you can choose if you do manual install (not sure about grub). You can always uninstall one grub and install the other. grub legacy has not been maintained for years and is based on MBR partitions scheme (some addins for gpt on some versions). Ubuntu modified its grub legacy to see ext4 partitions with 9.04, but no one was centrally maintaining grub legacy for years.

---

### Post by WorMzy on 2010-05-08
I find it's best to think of grub as something separate to Ubuntu. It doesn't care what version of Ubuntu (or any other distro) you're running so long as it's told where it's files are kept. Bearing that in mind, it should be possible to remove grub2 (sudo apt-get --purge remove grub-common) and install grub-legacy (sudo apt-get install grub), with absolutely no consequences. You will, however, need to install grub to the mbr, as "removing" grub2 will not delete it from the mbr.

So once you've installed grub-legacy, open a terminal and run grub, set the root to the right partition, and install it to the right disk's mbr. Follow this guide if you need help: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) (scroll down to the section entitled "How to restore the Ubuntu grub bootloader (9.04 and older)")

Please note that this is only a theory. I have not tried this as I already use grub-legacy left over from a 9.04 install.

---

### Post by Ordes on 2010-05-08
everything is basiclly said. 

Just be careful when u run a ext4 filesystem (for system). As far as i know grub-legacy doesnt support ext-4.

---

### Post by WorMzy on 2010-05-08
My grub-legacy is installed on an ext3 partition, and it finds my ext4 partitions kernels fine. But it might be problematic to have the stages stored on an ext4 partition, that's something I hadn't considered. If that is the case, then it may be worth creating a separate boot partition with ext3 as the file system.

---

