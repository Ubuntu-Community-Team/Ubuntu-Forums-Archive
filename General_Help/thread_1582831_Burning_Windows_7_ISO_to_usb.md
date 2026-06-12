---
title: "Burning Windows 7 ISO to usb?"
date: 2010-09-27
forum: General Help
---

### Post by kirbatron on 2010-09-27
I have the windows 7 iso and would like to burn it to usb so i can dual boot. can I burn the iso to the usb in ubuntu? imma n00b, any help appreciated. Thanks.

---

### Post by mendhak on 2010-09-27
Hi, yes it's possible.  Search for 'unetbootin' and install it.  Plug your USB stick in, then start unetbootin and it should detect it.  Then specify the location of your Win 7 ISO and that should be it.

---

### Post by mendhak on 2010-09-27
I forgot to mention - search Synaptics Package Manager for unetbootin or try

sudo apt-get install unetbootin  

You should then find it in System Tools in the menus, I believe.

---

### Post by kirbatron on 2010-09-27
Thanks, much appreciated! Also know of any place I could learn more about bash scripting and how ubuntu/linux work on a deeper more complex scale?

---

### Post by mendhak on 2010-09-27
No worries.

I'm new to Ubuntu too, and I'm currently learning bash from this website:

[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

Don't be tempted to jump ahead, try everything it tells you and you'll start 'realizing' how different it is from .bat files.

---

### Post by bayoffire on 2010-10-21
> **mendhak said:**
> I forgot to mention - search Synaptics Package Manager for unetbootin or try

sudo apt-get install unetbootin  

You should then find it in System Tools in the menus, I believe.

This does not work!

unetbootin is only for installing linux. Not windows!

---

### Post by a.sarkar on 2010-10-21
> **bayoffire said:**
> This does not work!

unetbootin is only for installing linux. Not windows!

According to [COLOR=Red]_[this]("http://www.addictivetips.com/windows-tips/install-windows-7-from-usb-drive-requires-2-simple-steps/")_[/COLOR] site unetbootin should work for windows too. However, there's a caution that if unetbootin doesn't work, then [COLOR=Red]_[Windows 7 USB tool]("http://wudt.codeplex.com/")_ [/COLOR]should work which happens to be a windows software.

---

### Post by Mark Phelps on 2010-10-21
From the unetbootin website:

> UNetbootin allows you to create bootable Live USB drives for Ubuntu, Fedora, and other Linux distributions without burning a CD.

Last time I checked, Windows 7 was not one of the "other Linux distributions"!

If you want to create an installable image of Win7 on USB stick, you would better going to an Win7 forum and asking THEM -- recommend sevenforums.com.

Realize, though, they will tell you how to do that using MS Windows.

---

### Post by C.S.Cameron on 2010-10-21
I have not found a method to run Win 7 from flash drive but you can install from flash drive:

Format drive NTFS (gparted).
Set boot flag, (gparted).
Copy files from Win 7 disk or extract from Win 7 iso.

---

