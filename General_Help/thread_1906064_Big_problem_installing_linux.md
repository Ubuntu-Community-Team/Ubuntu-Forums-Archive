---
title: "Big problem installing linux"
date: 2012-01-08
forum: General Help
---

### Post by Jean_Baptiste on 2012-01-08
I cant seem to install any linux distro, ive tried: ubuntu,kubuntu,opensuse and mageia linux. Both 32 and 64 bit. Most of the time the screen goes black and text says "no signal" after i press "install linux" in the cd boot menu. Every time ive "Try linux without installing" it works. I finally managed to get it to install (Mageia linux 64bit) but after i rebooted it would stop after 1 second when i see the login screen ( Cant move mouse or do anything). Its a very strange problem because those 2 seem to be different issues. Here is my hardware:
Ati Radeon hd 5770
AMD Phenom II x6 1055T
8192 DDR3
Asus M4A87TD
SAMSUNG HD103SJ ATA Device (1000GB)
I would be very thankful if i can get help since i hate using windows and want to get linux asap :))

---

### Post by thomsmells on 2012-01-08
Have you tried doing it from the desktop when inside the 'try without installing' option? Worked for me.

---

### Post by oldfred on 2012-01-08
I know this helps on nVidia video issues, not sure about ATI.

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

These may also work. Sometime generic if specific entry does not work.
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by silverhaze06 on 2012-01-08
> **Jean_Baptiste said:**
> I cant seem to install any linux distro, ive tried: ubuntu,kubuntu,opensuse and mageia linux. Both 32 and 64 bit. Most of the time the screen goes black and text says "no signal" after i press "install linux" in the cd boot menu. Every time ive "Try linux without installing" it works. I finally managed to get it to install (Mageia linux 64bit) but after i rebooted it would stop after 1 second when i see the login screen ( Cant move mouse or do anything). Its a very strange problem because those 2 seem to be different issues. Here is my hardware:
Ati Radeon hd 5770
AMD Phenom II x6 1055T
8192 DDR3
Asus M4A87TD
SAMSUNG HD103SJ ATA Device (1000GB)
I would be very thankful if i can get help since i hate using windows and want to get linux asap :))

I was having the same problem when I would boot up linux with a usb mouse or keyboard plugged in. But for me it just went away on its own. 

It could also be you need to activate the ATI/AMD Proprietary FGLRX graphics driver. when I first installed ubuntu my screen would go blank at login but wouldnt freeze. I then plugged it into my tv via HDMI and was able to see the desktop on there and activate the drivers so everything would work. then following this thread made everything work better. [http://ubuntuforums.org/showthread.php?t=1857911]("http://ubuntuforums.org/showthread.php?t=1857911")

but if that is not your problem try booting up with no usb devices plugged in to your computer.

---

### Post by silverhaze06 on 2012-01-08
> **Jean_Baptiste said:**
> I cant seem to install any linux distro, ive tried: ubuntu,kubuntu,opensuse and mageia linux. Both 32 and 64 bit. Most of the time the screen goes black and text says "no signal" after i press "install linux" in the cd boot menu. Every time ive "Try linux without installing" it works. I finally managed to get it to install (Mageia linux 64bit) but after i rebooted it would stop after 1 second when i see the login screen ( Cant move mouse or do anything). Its a very strange problem because those 2 seem to be different issues. Here is my hardware:
Ati Radeon hd 5770
AMD Phenom II x6 1055T
8192 DDR3
Asus M4A87TD
SAMSUNG HD103SJ ATA Device (1000GB)
I would be very thankful if i can get help since i hate using windows and want to get linux asap :))


Asus computers are also pretty buggy with linux at first, but they can be fixed. Try this section of the forum, all for problems with asus computers. you might have some luck there.[http://ubuntuforums.org/forumdisplay.php?f=408]("http://ubuntuforums.org/forumdisplay.php?f=408")

---

### Post by silverhaze06 on 2012-01-08
but then again, if all versions do not work for you, have you tried installing linux with an "alternate installer" cd? that might also work.

---

### Post by Jean_Baptiste on 2012-01-09
I dont think the problem is too high resolution since with mageia linux you can choose the resolution in the installer. And if the problem is with video card why was i able to install it once? shouldnt it either always fail or always work. I also tried the nomodeset or something with kubuntu and it didnt change anything, after i press "install linux" it would turn off monitor in a second or during the loading screen.

---

### Post by silverhaze06 on 2012-01-09
> **Jean_Baptiste said:**
> I dont think the problem is too high resolution since with mageia linux you can choose the resolution in the installer. And if the problem is with video card why was i able to install it once? shouldnt it either always fail or always work. I also tried the nomodeset or something with kubuntu and it didnt change anything, after i press "install linux" it would turn off monitor in a second or during the loading screen.


I had the same exact problem too. Its something with all the newer AMD based CPU'S/Graphics and ubuntu not being legally able to include proprietary drivers with their free software.

Me, I have an AMD A6-3400M APU with Radeon HD 6520G graphics. But I also have an HDMI port so I plugged that into my tv and everything showed up there. When I logged in the additional drivers window showed up and I activated the ATI/AMD proprietary FGLRX drivers. once I did that my screen started working right away. There is also a post update driver that is better but no one seems to be able to install from the additional drivers window.

So after that, if you want to get the most out of your card, follow this thread to get the better drivers working. [http://ubuntuforums.org/showthread.php?t=1857911]("http://ubuntuforums.org/showthread.php?t=1857911")

---

### Post by imachavel on 2012-01-09
try and list this:

sudo lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV730XT [Radeon HD 4670]
01:00.1 Audio device: ATI Technologies Inc RV710/730
03:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)


but your version. Sorry I'm not very familiar with the linux command line. One thing I did prefer with windows vs linux is that you can open device manager with windows. Then just download and install any necessary drivers. With linux  sometimes I believe you download the driver you need off the site, then see if you can go to system settings> then try and install restricted drivers. There is probably a command for this as well, but I don't know what it is, try this:

sudo apt-get update $ sudo apt-get install linux-restricted-modules-generic restricted-manager 
$ sudo apt-get install xorg-driver-fglrx 
$ sudo depmod -a 



I haven't tried those commands myself though

---

### Post by Jean_Baptiste on 2012-01-09
Well how do you expect me to install additional drivers before i can even install the os? and i did that nomode thing which should work no matter what your video card is and it still freezes.

---

### Post by silverhaze06 on 2012-01-09
> **Jean_Baptiste said:**
> Well how do you expect me to install additional drivers before i can even install the os? and i did that nomode thing which should work no matter what your video card is and it still freezes.

they are drivers for linux so they have to be installed after you install the os. I was having those problems too until i used the alternate ubuntu installer for amd 64 and just installed linux as the only operating system. but before you do this, if you still have windows installed burn your recovery media to disk. Here are the instructions on how to do that from the MS website, > 

To create a system repair disc

1.Open Backup and Restore by clicking the Start button , clicking Control Panel, clicking System and Maintenance, and then clicking Backup and Restore.

2.In the left pane, click Create a system repair disc, and then follow the steps.   If you're prompted for an administrator password or confirmation, type the password or provide confirmation.

And here is the torrent link to download the alternate amd installer, [http://releases.ubuntu.com/11.10/ubuntu-11.10-alternate-amd64.iso.torrent]("http://releases.ubuntu.com/11.10/ubuntu-11.10-alternate-amd64.iso.torrent")

But if you want to try and do a dual install of windows and linux easily, here is the torrent link for the AMD version of the desktop installer. [http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-amd64.iso.torrent]("http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-amd64.iso.torrent")

---

### Post by imachavel on 2012-01-09
does windows definitely need to be repaired? Interesting I've never done it like that. I've always just manually backed up the files, then to repair the installation I put the windows cd into the drive, boot to it, select the install, then select second option to repair after the windows files have loaded. Also, isn't that safer? Considering if the repair fails, then you need the disk for a fresh install.

I have a question I'd like to ask for future reference, the same way you can install windows from the ubuntu desk top by clicking on install side by side, can you install windows from the ubuntu desk top so it partitions off automatically? THanks

---

### Post by silverhaze06 on 2012-01-09
> **imachavel said:**
> does windows definitely need to be repaired? Interesting I've never done it like that. I've always just manually backed up the files, then to repair the installation I put the windows cd into the drive, boot to it, select the install, then select second option to repair after the windows files have loaded. Also, isn't that safer? Considering if the repair fails, then you need the disk for a fresh install.

I have a question I'd like to ask for future reference, the same way you can install windows from the ubuntu desk top by clicking on install side by side, can you install windows from the ubuntu desk top so it partitions off automatically? THanks


As long as windows is starting up and working fine it shouldn't need to be repaired. But if you are trying to undo the partitions that the failed installations made, then yes. The easiest thing to do would be to repair or re-install windows if the repair option won't work.. 

I would try the desktop amd version first so you still have windows. I would only use the alternate installer as a last resort. As far as I know you can only dual boot when windows is installed first. But if you have to use the alternate installer, you can use the Sun VirtualBox program and your windows cd to install windows as a virtual machine, but it wont be a true dual boot.

---

### Post by Jean_Baptiste on 2012-01-10
Im gonna try dual booting

---

### Post by Jean_Baptiste on 2012-01-22
Ok i managed to install debian!!! Everything works fine except when i install fglrx r6xx - r7xx ati proprietary drivers. After i reboot then the screen goes black i think just before login screen. Could it be that r6xx - r7xx mean newer video card than my radeon hd 5770???? or what is the problem?

---

### Post by silverhaze06 on 2012-01-22
> **Jean_Baptiste said:**
> Ok i managed to install debian!!! Everything works fine except when i install fglrx r6xx - r7xx ati proprietary drivers. After i reboot then the screen goes black i think just before login screen. Could it be that r6xx - r7xx mean newer video card than my radeon hd 5770???? or what is the problem?


your card should be supported. i had the same problem too before i installed the fglrx drivers. what i did was hook up my computer via hdmi to my tv so i could see everything. after enableing the drivers my screen started working. following this thread also helps. [http://ubuntuforums.org/showthread.php?t=1857911]("http://ubuntuforums.org/showthread.php?t=1857911")

---

### Post by Jean_Baptiste on 2012-01-22
THank you silverhaze! Ill try it within a week

---

### Post by Jean_Baptiste on 2012-02-01
Ok i installed debian stable and it works, however after i installed the newest proprietary drivers, everything became sluggish, moving folders is extremely slow etc. Without those drivers teeworlds (2d video game) runs extremely sluggish. After i installed proprietary drivers it wont even start. I thought all this has to do with debian so i installed ubuntu 11.10. It installed fine until it asked me to remove disk and reboots. Then it got stuck on the boot screen (I can only see purple) On debian forums someone said to try plugging it to hd tv with hdmi, didnt work.

---

### Post by Jean_Baptiste on 2012-02-01
Guess i have no choice but to go back to windows. I think linux developers first priority should be to get it working on every single system and hardware like microsoft does. Instead of focusing on some ****** unity crap.
I understand the unity is made because they want to appeal to wider audience, which is good thing. However i think this problem like mine has caused more problems because there is tons of people who want to try linux but because it wont install/work on their computer they just go back to windows.

---

