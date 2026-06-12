---
title: "Can't find ubuntu after install windows 7"
date: 2012-01-31
forum: General Help
---

### Post by jibon_24 on 2012-01-31
Hello everyone,
I have installed ubuntu 11.10 & windows 7 in my laptop. Due to crash of window 7 i need to install it again. But after that i don't see any option for starting ubuntu during boot time. Is there any way to get ubuntu again without reinstall it because i have no backup cd for ubuntu. Thanks in advance.

---

### Post by Lars Noodén on 2012-01-31
Windows does not play nice with other operating systems.  You might look here, though it will require a CD:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[https://help.ubuntu.com/community/WindowsDualBoot#Install_Ubuntu_after_Windows](https://help.ubuntu.com/community/WindowsDualBoot#Install_Ubuntu_after_Windows)

What apps are still holding you back on Windows?

---

### Post by jibon_24 on 2012-01-31
Thanks a lot for ur support. I will try it. This isn't for me but for one of my friend who r new in ubuntu & want to take the test of it. Hope he will leave windows soon.

---

### Post by sunewbie on 2012-01-31
If you are not able to locate ISO file of Ubuntu 11.10 and if you do not want to download 700Mb again, you can try gparted live CD to boot and then reinstall grub from the links given above,

I also found a simple explanation [here]("http://community.linuxmint.com/tutorial/view/245")

(hope mods do not mind link to Linux Mint)

basically, you need to install windows first and then any linux distro.

GRUB, boot loader for Linux, ubuntu identifies any OS including windoz, but Windows boot loader is not as friendly as GRUB and does not identify any OS and does not read ext3, ext4 partition (thought some tools are available, better used for read only ext3 from windows xp). Windows only wholeheartedly detects it's OS e.g. XP vista and 7.

Boot loader is in MBR and when you install GRUB, it gets over writen, but detects XP / 7. When you reinstall win 7, MBR gets re-written with windows boot loader, which does not detect Ubuntu.

If your friend does not want to loose windows or wants to keep it safe, you can use grub repair by yannbuntu. Some prefer easyBCD in win 7, which you need to install inside win 7 and it detects Linux OS. So, in future, if your friend removes Ubuntu, he can still boot into win 7. Alternatively, you can use 'repair' utility in win 7 to make win 7 boot again. I have XP and do not use easy BCD, so cannot help you if you ar stuck up, but I found a blog who was suggesting this use. If I find the link, I will come back again.

---

### Post by sunewbie on 2012-01-31
ok, I managed to find the links in lunch time

Install using EASY BCD 
[http://www.linuxbsdos.com/2011/06/11/dual-boot-linux-mint-11-and-windows-7/](http://www.linuxbsdos.com/2011/06/11/dual-boot-linux-mint-11-and-windows-7/)

gparted LIVE CD

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

download link

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

You can also use [Super GRUB disk]("http://www.supergrubdisk.org/") or Rescatux

Best is to follow official documentation / or link I gave you, which leads to Mint tutorial

Please note: A simple error I did when reinstalling grub2 was I selected sdA5.

You have to select sdX i.e. sdA and not sdXY i.e. sdA1 or sdA5, etc.

SdA is the first HDD (incase you have 2 HDD.

Hope this helps.

---

### Post by jibon_24 on 2012-01-31
Thank you all for ur support...;-)

---

