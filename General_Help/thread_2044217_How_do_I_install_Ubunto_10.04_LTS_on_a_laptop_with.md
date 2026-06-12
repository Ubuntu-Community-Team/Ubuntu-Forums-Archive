---
title: "How do I install Ubunto 10.04 LTS on a laptop without a CD/DVD and No Network?"
date: 2012-08-19
forum: General Help
---

### Post by Nap_BlownApart on 2012-08-19
Hi,
  I'm trying to install Ubuntu on a Samsung laptop that doesn't have a CD/DVD drive, and I don't have it connected to the network either (only wireless available on the laptop atm, but as there are no drivers installed, I can't use it.  And I'm connecting to the net via my iphone [no iTunes installed yet] so I cannot connect via the ethernet port.)

I'm following the [Fix for Ubuntu 10.04 Server USB Install]("http://blog.smalleycreative.com/linux/fix-for-ubuntu-10-04-server-usb-install/") guide but don't understand where I need to put the line:```
cdrom-detect/try-usb=true
```What file on the USB memory stick do I need to update with this entry?  (syslinux.cfg?)  (Or WHEN do I press F6??)

Somehow I got past this problem (once, had to reboot and now I can't get past the CD problem) and arrived at another one, where it's asking for a mirror.  As I'm not connected to the net, but the ISO contains all the packages, why is the installer insisting I nominate a mirror?
(This is a secondary issue as I've gone to a friends place and plugged in there.)
What is the path to the USB drive package repositry? (/dev/????  or /media/???  I don't know)

Cheers,
Nap

---

### Post by Wim Sturkenboom on 2012-08-19
Just for the first question

Boot your system; press <esc> immediately after the POST is finished (or just before it finishes). You should get the grub boot menu. Press 'e' and modify the line that looks like

```

linux /boot/vmlinuz-2.6.32-5-686 root=UUID=4e8c9e38-845f-435a-b24a-ef8c37cba4a2 ro  quiet splash

```

to

```

linux /boot/vmlinuz-2.6.32-5-686 root=UUID=4e8c9e38-845f-435a-b24a-ef8c37cba4a2 ro  quiet splash *[COLOR="Red"]cdrom-detect/try-usb=true[/COLOR]*

```

Next press <ctrl>X to boot.

This is a non-permanent change.

---

### Post by Nap_BlownApart on 2012-08-19
When I press it very quickly after/during the POST, I get the POST info that's normally hidden from view  (ie.  how much ram I have, mouse initialized, etc)

Then I get to the Boot Menu (still part of the POST function), which allows me to choose which drive to boot from.  USB is top of the list.

After selecting USB, I press <Esc> again, and at the top of the screen I get:
```
SYSLINUX 4.03 2010-10-22 EDD Copyright (c) 1994-2010 H. Peter Anvin et al aborted.
boot:
```
I tried entering the command but it says "Could not find Kernel image: cdrom-detect/try-usb=true".

It then proceeds to the **UNetbootin** screen, with 12 options, 1st is Default, 2nd is Help, 3rd is Install Ubuntu Server ....

When I press ESC after the post, I get the boot: prompt at the bottom of the screen this time, and the same happens when I enter the command as earlier.


=================================

In the UNetbootin menu, there is an option to do a 'Command-line install' (I actually want the Install Server option).  This is how I got past this b4, but got stuck on the network problem.
Going down this path, my network card is now configured (as I'm plugging into my friends lan), using DHCP, (I enter the hostname for the machine) and I'm then asked for a mirror to which I select the default suggestion (being in australia).  The screen goes blue except for a white line at the bottom and a black cursor on its left (I can see my typing in the white area).
Nothing seems to be happening now.  There isn't any network activity going on according to the router.

arrrggggg

---

### Post by mastablasta on 2012-08-19
you post is confusing with no details on the machine at all.

what you do is set the device to boot from USB. once it botos form USB you install the os. once the OS is installed you need to connect via cable to internet to get the drivers for it. and that's it.

---

### Post by Nap_BlownApart on 2012-08-19
It's a Samsung N145 Plus Laptop.  It runs x86 code.
The installer is working, just that it insists on searching for a CD that is not there.
The DHCP config works ok, but it can't get to the mirror site.  Just sits there with a blank screen.

I'm not in the mood for trolls, so if you can't offer a possible solution, find somewhere else to post please.

---

### Post by mastablasta on 2012-08-20
> **Nap_BlownApart said:**
> It's a Samsung N145 Plus Laptop. It runs x86 code.
The installer is working, just that it insists on searching for a CD that is not there.

It shouldn't do that. it should search for them on USB.
 
The menu you name as unebootin menu is probably, actually a grub menu. unetbootin only copies the files on USB and makes it bootable AFAIK. and here is how you handle boot options: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
i've installed 2 maschines with USB and neither of them was searching anything on a CD.
 
if the soruces are really pointed to a CD you can change that in sources file
since you are using CLI interface look for instructions here: 
[https://help.ubuntu.com/community/SourcesList](https://help.ubuntu.com/community/SourcesList)
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
 
 
> 
The DHCP config works ok, but it can't get to the mirror site. Just sits there with a blank screen.
.
 
 
it tries to connect to mirror because it received commands to update the OS. packages are on the media, however not all of them. and they've probably been updated since the the time the image was made.
 
 
have you though about giving it a go with desktop or alternate CD? Unless you need the server...
 
Additionally consider using version 12.4 instead (you can use Xubuntu if you don't like Unity interface) since it has numerous improvements, patches, bugfixes (ok some new bugs are introduced) and newer kernel (=newer drivers).

---

