---
title: "Boot problems"
date: 2012-04-01
forum: General Help
---

### Post by jonas01 on 2012-04-01
Hello everybody,

I am new here and I am a beginner of using Xubuntu (Linux at all), so pleace correct me if I write confusing things...

[B]My problem:
[/B]
Always when I will run my Xubuntu there is a error message* on my screen which means that I had a error with modprobe.
This error is alway when I boot the system. :confused:

I tried to install Xubuntu with WUBI, but when I will finish the insatallation and reboot, I will have this error message* . 

* error message = see the picture I had uploaded.

I couldn't install Xubuntu on the normal way, because after the menu with the diffrent choices for example "run as a live system" or "install Xubuntu" I will have the same error message, too.

**My system:**

_Partition 1:_
Windows 7 Home Premium - 64-Bit

[U]Patition 2:
[/U]Xubuntu 11.10 64-bit
(installed with wubi on Win7)

**Hardware:**

-AMD FX(tm)-4100 Quad-Core Processor (3,60 GHz)
-Nvidia gts 450
-Realtek High Definition Audio
-Optiarc DVD RW AD-5280s
-mouse (usb-device) msi (HID)
-keyboard (usb-device) msi (HID)
-Flatron IPS235 (PnP screen)
-Linksys Wireless-G PCI Adapter
-Realtek PCIe GBE Family Controller
-USB 3.0 on board
-extra usb-card with usb 2.0
-extra usb ports at the front (2.0)
-motherboard msi 990 fxa-gd 65
-12 GB Arbeitsspeicher
-1 TB HDD

I don't know what I should do because I don't understood the whole english things very well...

(A German user in an English world of konfiguration...:p)

---

### Post by sudodus on 2012-04-01
Welcome to the Ubuntu Forums, Jonas :-)

I think you should try again to boot from the Xubuntu install CD/USB drive. Test the system (that is run a live sesssion), do not install anything! At the first menu, try some boot options, for example nomodeset

See the following link
[[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

---

### Post by brainwash on 2012-04-01
This is a well-know issue. There is already a similar thread:

[http://ubuntuforums.org/showthread.php?t=1946307](http://ubuntuforums.org/showthread.php?t=1946307)


So you have to boot with **nomodeset** kernel parameter.

After installation of Ubuntu you should download and install the proprietary Nvidia driver (via Additional Drivers).

---

### Post by jonas01 on 2012-04-01
> **sudodus said:**
> Welcome to the Ubuntu Forums, Jonas :-)

I think you should try again to boot from the Xubuntu install CD/USB drive. Test the system (that is run a live sesssion), do not install anything! At the first menu, try some boot options, for example nomodeset

See the following link
[[COLOR=Red]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")
@sudosus
I can't start the system as a live system. I have the option to do this, but there is the same error message after a while.

How can I try the boot options (with your example "nomodeset"?) when there is no command line? Or should I write in this screen  (see my picture of the threat start)

When i reboot the whole system or start the whole machine new I will get the bootloader od microsoft with the options 
-Windows 7 Home Premium
-Xubuntu


when I choose Xubuntu there is in the screen a white written text like:

If you want to change installation or boot options press ESC
and the wit a coutdown of 10 secounds.

If I press the ESC-Button, I will get the same screen after a while with the error.



When i start the Xubunt as an iso file in a virtual machine there is no problem with running and so on...
I can do everything and Xubuntu works, but in the real machine there is the error....

---

### Post by jonas01 on 2012-04-01
> **brainwash said:**
> This is a well-know issue. There is already a similar thread:

[http://ubuntuforums.org/showthread.php?t=1946307](http://ubuntuforums.org/showthread.php?t=1946307)


So you have to boot with **nomodeset** kernel parameter.

After installation of Ubuntu you should download and install the proprietary Nvidia driver (via Additional Drivers).

I can't boot with the parameter nomodeset... Or I don't know how, but in the threat you linked me there was the correct way, but with grub2 as bootloader.

My bootloader is the Microsoft bootloader...
OMG... My brain is on the way to turn off... I have the same screen when I tried other linux distri...

How could I download the Nvidia files, when I am in the boot manager?
I have the right files "up to date" on the Win7 partition...

---

### Post by brainwash on 2012-04-01
[QUOTE=jonas01]My bootloader is the Microsoft bootloader...[/QUOTE]

So you are talking about your WUBI installation? There is a way to set the nomodeset paramter in this case:

[http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)

Read the instructions of **Method 2**.

---

### Post by jonas01 on 2012-04-01
> **brainwash said:**
> So you are talking about your WUBI installation? There is a way to set the nomodeset paramter in this case:

[http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)

Read the instructions of **Method 2**.

Ok, but there is now another problem:

the file wubildr-disk.cfg

do not exiost...

My file tree of the folder is this one:

**/ubuntu/**
*_files:_*
uninstall-wubi.exe
Xubuntu.ico
[U][I]folders:
[/I][/U]disks
install
winboot
--------------------------------------------------------------------------
[B]/ubuntu/disks
[/B][U][I]files:
[/I][/U]root.disk
swap.disk
_*folders:*_
boot

[B]/ubuntu/disks/boot
[/B]*_folders:_*grub

[B]/ubuntu/disks/boot/grub
[/B][I]#empty#
[/I]--------------------------------------------------------------------------
[B]/ubuntu/install
[/B]_*files:*_
installation.ico
MD5SUMS-metalink (definition of file-type is: file)
MD5SUMS-metalink.gpg
xubuntu-11.10-desktop-amd64.metalink

_*folders:*_
boot
custom-installation

[B]/ubuntu/install/boot
[/B]_*files:*_initrd.lzmd5sum.txt
vmlinuz (definition is: file)

_*folders:*_
grub

[B]/ubuntu/install/boot/grub
[/B]_*files*_[B][U][I]:
[/I][/U][/B]grub.cfg

[B]/ubuntu/install/custom-installation
[/B][U][I]files:
[/I][/U]preseed.cfg_*folders:*_hooks
packages[B]

ubuntu\install\custom-installation\hooks[/B]
_*files:*_
casper-premount.sh
early-command.sh
failure-command.sh
success-command.sh

**ubuntu\install\custom-installation\packages**
#empty#
--------------------------------------------------------------------------

[B]ubuntu\winboot
[/B]_*files:*_wubildr(file-type is: file)
wubildr.cfg
wubildr.mbr
wubildr.tar
wubildr-bootstrap.cfg


--> There is no wubildr-disk-cfg
...

---

### Post by sudodus on 2012-04-01
Some more suggestions:

1. Try if the instructions could apply to one of the [FONT=Courier New][SIZE=3]wubi...cfg[/SIZE][/FONT] files!

2. Do you have an install CD/DVD or an install USB drive? If you haven't tried CD/DVD, burn the iso-file onto a disk and try. That way you should get to the menu, where you can enter the boot options (nomodeset and the other options) according to the iink in post #2.

3. Try the beta version of Xubuntu Precise (12.04 LTS). It is already quite good, particularly recognizing hardware (which seems to be your problem with 11.10).

---

### Post by jonas01 on 2012-04-01
I used a Xubuntu 11.10 iso file which I burned to CD. It was a iso file from aDVD which is a DVD to a magazine for professional IT pasons which use Linux. the name of the magazine is:

"LINUX INTERN EXTRA Nr.2" So i only burned it to CD, and the Wubi was in this ISO, but this installation with the wubi didn't include the grub, or there is a programming mistake, so that there is no grub2 on the disk (but i don't think so).

I think the best way would be at the first to download the new version, then we can look for the next situation with the newest version...

Many thanks to everybody who wrote me up to now, I am happy to see that I am at the right place with my problem. I will download the ISO tomorrow, so today I will only thry the things the persons wrote before this entry...

---

### Post by brainwash on 2012-04-01
Ok, wubildr-disk.cfg is missing, so it's a 2-stage installation. This means you will have to press [ESC] after the Microsoft bootloader to get to the options menu.

In the options menu you mark the first entry (normal mode) and press E.

Now you add nomodeset to the end of the first line. Boot by hitting [CTRL]+X.

```
linux /ubuntu/install/boot/.......... quiet splash nomodeset
```

---

### Post by jonas01 on 2012-04-01
Do I need to have the CD in the computer for this step or is it working without a CD?

---

