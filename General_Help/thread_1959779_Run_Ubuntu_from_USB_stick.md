---
title: "Run Ubuntu from USB stick"
date: 2012-04-16
forum: General Help
---

### Post by dragossshadow on 2012-04-16
Hello fellows users of Ubuntu. I'm new here on the forums. I want to run Ubuntu from a USB stick. Why? I want to have a portable 'HDD' to run on friends computers. I would use a Live CD, but I want to save data on the stick.

---

### Post by Megaptera on 2012-04-16
Are you asking how to?
If so, two options explained here: [http://www.linuxcandy.com/2012/02/how-to-create-live-and-bootable-usb-for-ubuntu-11-10.html](http://www.linuxcandy.com/2012/02/how-to-create-live-and-bootable-usb-for-ubuntu-11-10.html)

---

### Post by oldfred on 2012-04-16
If flash drive is 4GB or less then Megaptera link should be good. You want the persistent feature to save some data.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

But if flash is 8GB or more you can do a full install. Or install a lighter weight version.

Installs to 4GB flash
HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

I have a full install of 12.04 on a 8GB partition. It is a little slow in loading the larger apps. But with enough RAM once loaded each app runs well.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

---

### Post by dragossshadow on 2012-04-19
Isn't there any automated option?

---

### Post by sudodus on 2012-04-19
> **dragossshadow said:**
> Isn't there any automated option?

The instructions in this link (at the end of the page) is actually rather simple to use. So if you already have Ubuntu, you can use the Startup disk creator.
[[COLOR="Red"]_http://testcases.qa.ubuntu.com/Install/DesktopLiveSession_[/COLOR]]("http://testcases.qa.ubuntu.com/Install/DesktopLiveSession")

If you have problems with that one, try Unetbootin!

It is a good idea to have a ***casper-rw partition*** instead of a casper-rw file. You create the partition(s) with Gparted.

---

