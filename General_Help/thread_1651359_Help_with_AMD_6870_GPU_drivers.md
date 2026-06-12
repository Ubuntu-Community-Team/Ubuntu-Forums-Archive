---
title: "Help with AMD 6870 GPU drivers"
date: 2010-12-23
forum: General Help
---

### Post by Rhodan on 2010-12-23
I have an AMD 6870 GPU, and a clean installation of Ubuntu 10.10.

I followed the instructions from this site to install the AMD 10.12 drivers:

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

What I did:

1)
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0

2)
sudo apt-get install ia32-libs

3)
sudo apt-get remove --purge xserver-xorg-video-radeon

4)
sh ati-driver-installer-10-12-x86.x86_64.run --buildpkg Ubuntu/maverick

5)
sudo dpkg -i fglrx*.deb

That all worked fine.

6)
Now when I try this, I am told the file does not exist:
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

7)
If I try this, 
sudo aticonfig --initial -f

It says:
aticonfig: No supported adaptaters detected


Any idea's on how to solve this?

---

### Post by PhantmKllr on 2010-12-23
AMD hasn't yet released the Linux drivers for your graphics card. So, you'll have to use the open source drivers.

---

### Post by Rhodan on 2010-12-23
They have released them:

[http://blogs.amd.com/play/2010/12/14/amd-catalyst%E2%84%A2-10-12-driver-%E2%80%93-what%E2%80%99s-new/](http://blogs.amd.com/play/2010/12/14/amd-catalyst%E2%84%A2-10-12-driver-%E2%80%93-what%E2%80%99s-new/)

[http://www.*****************/driver/articles/amd-catalyst-10-12-linux-driver-for-ubuntu-10-10-available.html](http://www.*****************/driver/articles/amd-catalyst-10-12-linux-driver-for-ubuntu-10-10-available.html)

---

### Post by PhantmKllr on 2010-12-23
That's a preview driver. It's not fully developed yet.

---

### Post by cascade9 on 2010-12-23
Dont you have to stop 'x' to get graphical drivers installed? Been a while since I install ATI drivers, but I though that it was a needed step.

> **PhantmKllr said:**
> That's a preview driver. It's not fully developed yet.

Its got to be better than using the 10.11 drivers. OK, this is ATI, it *should* be better than the 10.11 drivers BTW, the 10.11 drivers do work with the 6XXX cards, just you get an 'unsupported hardware' watermark.

---

### Post by Rhodan on 2010-12-25
With the 10.11 drivers I get a black screen when rebooting.

Has anybody got the new AMD 6850 / 6870 cards to work under Ubuntu 10.10 ?

---

### Post by cascade9 on 2010-12-26
Yes, look here- 

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1614444&page=4](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1614444&page=4)

olof_, post #38

I'm sure there are other people who've done it as well.

---

### Post by Rhodan on 2010-12-26
Thanks I'll have a look.

---

