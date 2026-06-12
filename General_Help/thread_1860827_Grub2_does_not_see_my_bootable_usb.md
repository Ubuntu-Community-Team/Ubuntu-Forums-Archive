---
title: "Grub2 does not see my bootable usb"
date: 2011-10-15
forum: General Help
---

### Post by khatru82 on 2011-10-15
Hi,
I have a desktop system with two disks; Kubuntu is installed on one of them, windows 7 on the other.
Like I used to do, I have created a bootable usb in order to replace Kubuntu with Ubuntu (11.10) but, when I reboot my system, the bootable usb drive is not considered at all by Grub2. I tried to use different sw like unetbootin and so on (as suggested by many forums) but nothing changes. I also installed grub on removable disk (as suggested by many forums) but it's always the same. I just wanted to remove Kubuntu and put on Ubuntu.

Sorry for my newbieness.

---

### Post by mister_playboy on 2011-10-15
The installer should take over during the booting process before you see GRUB pop up.

In your case it sounds like USB booting is not enabled in your BIOS.  Try pressing F2 or ESC on the first splash screen that appears after boot and take a look at your settings.

---

### Post by khatru82 on 2011-10-15
I did it, removable key is already the first choice for booting :(

---

### Post by varunendra on 2011-10-17
In some cases, it helps to change the USB key itself with a different brand/model. Some models are not bootable at all, while some other ones do not boot with some particular computers (perhaps a BIOS incompatibility).

If you have access to another computer (of different model), you should first try the USb on it to confirm if it is bootable at all. If the boot menu lists your USB key as a boot-device option, there is no reason why it should not boot on selecting it if it IS bootable. The hot key to bring up that boot menu can be different for different computers - typically F9, F10, F12, Esc, F8 etc.

---

### Post by khatru82 on 2011-10-21
Thank you, but I have already tried (unsuccesfully) with a different USB Drive. 
I suppose that first USB drive should be "bootable" since I already used it to install previous Ubuntu versions. This time I really don't know what's happened...I'm going to give up :(

---

### Post by philinux on 2011-10-21
> **khatru82 said:**
> Thank you, but I have already tried (unsuccesfully) with a different USB Drive. 
I suppose that first USB drive should be "bootable" since I already used it to install previous Ubuntu versions. This time I really don't know what's happened...I'm going to give up :(

I've had this. Not only did I have to set the boot priority as you have I also had to move the usb stick to the top of the list of hard drives. It loses this when there is no usb stick plugged in. It then shows it at the bottom of list of hard drives next time its plugged in.

---

### Post by khatru82 on 2011-10-23
Yes, it was the hard drives order! I supposed that the boot devices order was enough, but it was not. 
Thank you so much, I was able to replace my previous installation of Kubuntu with Ubuntu 11.10. 
I actually have chosen the replace option when installing, that is, the installation manager recognized a previous version of Ubuntu and suggested me to replace it with a new version. The installation terminated in a positive way but, when I rebooted the system, nothing happened. After the BIOS I see _**a black screen and nothing more**_. 

_Now I have no Ubuntu and no Windows_ :( :(

I just was able to start Ubuntu by the USB Stick in the try-me mode. 
I really do not know what is happening, I installed so many versions of Ubuntu so far...
Any suggestion please!!

---

### Post by varunendra on 2011-10-23
> **khatru82 said:**
> After the BIOS I see _**a black screen and nothing more**_. 

_Now I have no Ubuntu and no Windows_ :( :(
First, make sure to reset the hard drive order in BIOS to boot from the correct hard drive. If that is already correct, download [boot info script]("http://bootinfoscript.sourceforge.net/"), extract and run it as told on the download page and post the contents of RESULT.txt here (or [pastebin]("http://paste.ubuntu.com/") the contents and post only its link here to save server space on forums).

---

### Post by khatru82 on 2011-10-25
Hello, finally it worked. It was the hard drives order in the BIOS menu that was incorrect, probably due to the change I applied in order to give priority to the USB device.
Thanks to everybody for precious support!

---

