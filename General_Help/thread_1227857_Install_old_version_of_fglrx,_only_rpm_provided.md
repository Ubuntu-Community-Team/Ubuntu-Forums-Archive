---
title: "Install old version of fglrx, only rpm provided"
date: 2009-07-31
forum: General Help
---

### Post by Jeinhor on 2009-07-31
Hi,

I would like to install the proprietary graphic driver fglrx to get rid of some display problems. Problem is I have a old card, not supported by the newer versions of fglrx (Radeon 9200).

If I go to ati.com, I eventually land at this page: [http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx](http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx).

As Ubuntu is using X.org, the only option is a rpm file. Would it work just converting this rpm file with alien, like so: [http://embraceubuntu.com/2005/09/23/installing-using-an-rpm-file/](http://embraceubuntu.com/2005/09/23/installing-using-an-rpm-file/)

Thanks in advance!

---

### Post by realzippy on 2009-07-31
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.28.8.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.28.8.run)  

is also offered.
xxxxx.run  packages are for debian/ubuntu,

but,do you run 64bit?If not,this driver is yours:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run)

---

### Post by Sepanderi on 2009-07-31
> **Jeinhor said:**
> As Ubuntu is using X.org, the only option is a rpm file. Would it work just converting this rpm file with alien, like so: [http://embraceubuntu.com/2005/09/23/installing-using-an-rpm-file/](http://embraceubuntu.com/2005/09/23/installing-using-an-rpm-file/)

Seems so. Here's even a bit newer post: [http://www.kartook.com/2009/05/18/installing-using-an-rpm-file-on-ubuntu-904/](http://www.kartook.com/2009/05/18/installing-using-an-rpm-file-on-ubuntu-904/)

So I'm guessing that's still quite valid way to go. Shouldn't take much time at all to test. :)

---

### Post by realzippy on 2009-07-31
again,you do NOT need to use a rpm.file,,,,,,,,,,!

---

### Post by t0p on 2009-07-31
> **Jeinhor said:**
> Would it work just converting this rpm file with alien, like so: [http://embraceubuntu.com/2005/09/23/installing-using-an-rpm-file/](http://embraceubuntu.com/2005/09/23/installing-using-an-rpm-file/)


Not all *.rpm*s will convert to working *.deb*s with alien.  But I haven't come across an *.rpm* yet that it doesn't work for.  So try it.

I'm surprised you even felt the need to ask this question.  If alien doesn't work with this *.rpm*, what have you lost by trying?

---

### Post by realzippy on 2009-07-31
> **t0p said:**
> Not all *.rpm*s will convert to working *.deb*s with alien.  But I haven't come across an *.rpm* yet that it doesn't work for.  So try it.

I'm surprised you even felt the need to ask this question.  If alien doesn't work with this *.rpm*, what have you lost by trying?


All this might be true.Sometimes I wonder why people post here;is it for the beans or dont they have somebody to talk to??
There is absolutely no need to convert an ati.rpm to make the ati driver to work in ubuntu.Nor does it help a beginner....

---

### Post by danwood76 on 2009-07-31
What version of Ubuntu are you using?

The older fglrx will not work with newer Ubuntus as Ati write each driver for certain kernel versions and X11 versions.

But in the older cards the Xorg ATI and Radeon drivers should be perfectly fine.
I use the radeon driver on my x1950 and I have a nice large desktop and have full accereration etc without issues.

---

### Post by martinbaselier on 2009-07-31
This guide probably provides a better solution for what you want to achieve. 

[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

---

### Post by Jeinhor on 2009-09-02
> **t0p said:**
> Not all *.rpm*s will convert to working *.deb*s with alien.  But I haven't come across an *.rpm* yet that it doesn't work for.  So try it.

I'm surprised you even felt the need to ask this question.  If alien doesn't work with this *.rpm*, what have you lost by trying?

Well, at my friend's HTPC we tried installing some new graphic drivers, which crashed the system and after reboot we couldn't start X anymore. We had to re-install the system.

Therefore, I first wanted to check if I was even remotely proceeding in the right direction.. of course I could just test, but I've spent several hours configuring this system and would rather NOT re-install it.

> **realzippy said:**
> All this might be true.Sometimes I wonder why people post here;is it for the beans or dont they have somebody to talk to??
There is absolutely no need to convert an ati.rpm to make the ati driver to work in ubuntu.Nor does it help a beginner....

As I don't how RPM and DEB relates I thought I should ask before doing anything stupid. Sorry if I made you upset...


Thank you for all tips! After reading your posts I decided to not install, and instead buy a new graphics card if I can't live with the current graphic problems.

---

### Post by sideaway on 2009-09-02
can't use fglrx in 9.04... you know that right? Need wither a HD radeon, or the radeomhd drivers.

---

