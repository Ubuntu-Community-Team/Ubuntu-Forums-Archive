---
title: "find / boot / grub / stage1 Error 15 File Not found. Tried for Hours...HELP!!!"
date: 2011-10-30
forum: General Help
---

### Post by NotSoSiniSter on 2011-10-30
So when I got a new laptop, I decided to install linux on my old one for kicks. Its not a bad computer, only a year old, just needed more beef. :D So, I wiped windows 7 and installed Linux 11.04. A week later the 11.10 update came out, and I updated. Today, I wanted to dual boot with Linux and Windows 7. So, after some forum reading, I downloaded Gparted and dropped it on a USB drive. (My old computer doesn't have a CD Drive) booted up, split the hard drive in half, no problems. I booted back into linux and everything was fine. I installed Windows 7 from a usb stick onto the empty partition. Everything went well. :D But...grr...

So as I understand it, I have to repair the Boot Manager because Windows 7 overwrites it. So I followed the instruction on this page to restore the boot manager: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5) The problem that I've been stuggling with it for well over 2 hours!! I type root (hd0,0) no errors or anything. Then I type setup (hd0) it checks if it can find /boo/grub/stage one. and it says NO. As the post title shows, I also tried the "find / boot / grub / stage1" and it turns up NOTHING. It seems that grub is not installed? I think I installed it from the ubuntu live CD. But maybe I did it wrong? I tried mounting the partition as someone suggested on this forum and it did nothing! D: 

Thank you!!! I got my liveUSB 11.10 stick ready to be fired up. :D

---

### Post by nerdy_kid on 2011-10-30
Those instructions are for grub 1, not for grub 2 which is what Ubuntu 11.04 uses.  Try following these instructions:  [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Good luck!

---

### Post by NotSoSiniSter on 2011-10-30
Haha that would help! :D Thanks, but...still not working... D: 

this fdisk -1 thing, is it just to know what disk is what right? I can't get it to list anything. I looked in gparted and it listed everything. Hope I can do it that way. :D

So I went through each of these commands, 

sudo mkdir /media/sda# 

I take it that the "#" in this line is to be my Linux HDD? For me its sda1. So I typed that line with sda1. But then it gave me an error "cannot creat directory /media/sda1: file exists" I think I did it a few times? So I just kinda went on.

sudo mount /dev/sda# /media/sda#

I think the /dev/sda# is suppose to be the bootloader? The bootloader is the 100mb partition that windows 7 made right? For me that one is sda2. So the command I typed was sudo mount /dev/sda2 /media/sda1 

sudo grub-install --root-directory=/media/sda# /dev/sda#

I tried various "sda#"s until I got used 1 for the first # and 2 for the 2nd. It then said "Probing devices to guess BIOS drive. This may take a long time. /Next line/ The file /media/sda1/boot/grub/stage1 not read correctly.

So...um...help? I don't know whats going on. Terminal window is still open, waiting for instruction. :D :D

---

### Post by NotSoSiniSter on 2011-10-31
bump

---

### Post by Justinba1010 on 2011-10-31
Its "Ubuntu 11.10, not Linux 11.10" Linux is the core of Ubuntu, but Ubuntu is not Linux, neither vice versa.

---

### Post by Justinba1010 on 2011-10-31
Also a clean reinstall should fix it. 

Try if it was the architecture. If its 64 Bit get Ubuntu 64 Bit. 32 etc. 
I dont think its worth the trouble on a new install.

---

### Post by nerdy_kid on 2011-11-01
Turn the affected computer all the way off, and then boot off of the usbstick. Try the instructions I linked again, posting the output of each command.

---

