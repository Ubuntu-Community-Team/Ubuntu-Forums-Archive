---
title: "Netbook won't boot from USB"
date: 2010-04-24
forum: General Help
---

### Post by Robdemo on 2010-04-24
I downloaded both unetbootin-liux 433 and Ubuntu-9.10-netbook-remix-i386.iso onto a USB Flash drive. My MSI U160 netbook has Windows 7 Starter. I checked Startup and found three USB boot options: USB Hard Drive, USB CD/DVD,and USB Floppie, along with plain old Hard Drive. I put the USB Hard Drive as Option #1. I plugged in my USB Flash Drive and tried to boot. The USB blinked a few times but my Netbook booted to Windows. 
I read all the pages of UNR info I could find and treid several tweeks like  "Install -mbr /dev/sdb1" but got message that needed destination file which I didn't know. I am not very computer literate so badly need help to get off Windows and back to Linux as I have on my desktop. What can I do now???

---

### Post by cogier on 2010-04-24
I looks as if you have just copied the file to your USB stick. That wont work. You need to install the ISO on to the USB stick.

If you can load a live Ubuntu CD then you can go to **System>Administration>USB Startup Disk Creator** and using your .iso file create the bootable image. There is a tool to do this for Windows if needed here [http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe]("http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe")

---

### Post by FrPaulB on 2010-04-24
Is unetbootin on the USB drive you are trying to use to boot from? That's not how I believe it works. I think (I have used it like this) you need to have it installed on a working system, either windows or Linux. You run Unetbootin and that will then create a bootable USB drive. You can either let Unetbootin download the .iso file of the distro you want, or you can download the distro you want first and use the .iso option. I have had more success using the latter way.

It effectively takes an image of a CD and writes it to the USB drive drive in the way a CD would be created.

---

### Post by Robdemo on 2010-04-24
Thanks much. I am now loading the USB creator which seems to take quite awhile. Robdemo

---

