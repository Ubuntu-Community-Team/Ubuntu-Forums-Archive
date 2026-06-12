---
title: "unetbootin doesn't work"
date: 2011-05-25
forum: General Help
---

### Post by indianhits on 2011-05-25
Hello guys i am trying to install ubuntu 11 and i am trying to create a live USB (using unetbootin )before installing in my HDD so i followed all the instruction and when i rebooted my system it shows me boot menu and it only shows me default option in the menu nothing else is there.when i press ESC it shows me "BOOT:".  What is the problem???  and again i tried to use the tool but i formatted the 2GB USB using FAT32 and then when i tried to install it show only 4 files and none of the ubuntu ISO files are there in the USB  BTW i am using Windows XP  i tried to use USB-creator in the iso file but it shows me Permission denied(yes i am running as Admin)  i also tried Universal-USB-Installer but it shows me "Data Broken in "casper\filesystem.squashfs" File is broken"  As you can see i have tried all the ways Please help me.Thanks!

---

### Post by ~!geek!~ on 2011-05-25
Use universal usb installer :
[http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe)

Windows xp says permission denied.. It is the time to move to ubuntu completely :)

---

### Post by novinick on 2011-05-25
try this : get new version of unetbootin 
(not the one that exists in repos , since it may not support newer distros properly )

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) 

save ,unpack if needed , then change exec flag
 by chmod +x and double click on it

 [http://unetbootin.sourceforge.net/unetbootin-linux-latest](http://unetbootin.sourceforge.net/unetbootin-linux-latest) 
[http://unetbootin.sourceforge.net/unetbootin-windows-latest.exe](http://unetbootin.sourceforge.net/unetbootin-windows-latest.exe)
[http://unetbootin.sourceforge.net/unetbootin-mac-latest.zip](http://unetbootin.sourceforge.net/unetbootin-mac-latest.zip)

it has now a buld for aple mac  too :)

you may hava a antivir protection that denies writes to usb drive

---

### Post by indianhits on 2011-05-25
@geek i tried that its showing "Data Broken in casper\filesystem.squashfs.File is broken". @ novinick i am using the latest version and i have disabled antivirus(AVG) still its not working

---

### Post by novinick on 2011-05-25
it maybe some bug between ehci host controler 
and usb storage driver inside ubuntu 

have you tried this with ubuntu 10.10 or ubuntu 10.04 ?
to put it and boot it

reason is ,here similar problem>
[http://ubuntuforums.org/showthread.php?t=1767022](http://ubuntuforums.org/showthread.php?t=1767022)

you may also have broken usb flash drive , after some usage cells
on flash drives gets broken    *don know how to translate diferent

---

### Post by satanselbow on 2011-05-25
"Data broken" rather implies that your ISO is broken - did you check the MD5? That may also explain the rather overexcited XP "permission denied" message ;)

---

### Post by indianhits on 2011-05-26
oh no i have waited three exciting days to download ubuntu now everything has just shredded away.  i just checked MD5 and found that three files checksum doesn't match  1)filesystem.squashfs(which is >600MB) 2)bcmwl...deb 3)sl-modem-...deb  i guess i have to say goodbye to the file right?? cause i don't have a good internet speed.

---

### Post by mastablasta on 2011-05-26
iso is only one file. it's an image file of the CD.
 
yes you are done for now.
 
you could try bittorrent. transfer is safer and sometimes it can be faster on slow internet (how slow are we talking here, as bittorrent will get it down overnight on 256kB/s)
 
also bittorrent is doing the check as it is downloading the file.
 
Ubuntu used to have ship it service where they shipped a free CD but they don't have that anymore. :-(

---

### Post by indianhits on 2011-05-26
yeah shipit was really good....  i am downloading using proxy and it gives me 30-50kbps but it pauses and then i would have to resume it again i think this might be reason for corrupted ISO   BTW i am using proxy because my network doesn't allow to download files (above 2MB)so its a small trick.  is there any split files available for ubuntu that i can download???

---

