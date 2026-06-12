---
title: "Firefox and TB3 issues _ PLEASE HELP!!"
date: 2010-02-01
forum: General Help
---

### Post by jimmyUT on 2010-02-01
So I have Namoroka installed and want to get rid of in and install 3.6 on Karmic... I tried uninstalling from software manager, but namoroka is still here and that is what I am browsing with.  any ideas what I did wrong or how to fix?

---

### Post by lovinglinux on 2010-02-01
Namoroka is Firefox 3.6

See [this](http://lovinglinux.megabyet.net/?page_id=220#Installing-Other-Versions-1).

---

### Post by jimmyUT on 2010-02-01
I have ver 3.6.2pre  is that current stable version?

---

### Post by wojox on 2010-02-01
It looks like you have the nightly build installed. Do you remember installing any ppa's? Click on lovinglinux's link and there are a variety of ways for you to install.

---

### Post by jimmyUT on 2010-02-02
so what is the nightly build? would that have installed by installing pps for thunderbird 3.0.1?

---

### Post by crichard on 2010-02-02
> So I have Namoroka installed and want to get rid of in and install 3.6  on Karmic

try to uninstall firefox via Synaptic Package Manager. If you want to install firefox from [http://mozilla.com](http://mozilla.com), follow this[ pos]("http://surferzworld.com/?p=193")t.

For other options, have a look at this very useful [thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by lovinglinux on 2010-02-02
> **jimmyUT said:**
> so what is the nightly build? would that have installed by installing pps for thunderbird 3.0.1?

Yes, you probably have the [ubuntu-mozilla-daily PPA]("http://lovinglinux.megabyet.net/?page_id=220##3---Installation-from-PPA-repositories-3"). If you are using 32bit and want only stable versions than I recommend that you uninstall Thunderbird and Firefox, then remove the *ubuntu-mozilla-daily* ppa from your software sources (System >> Administration >> Software Sources), then install them again. This will revert to the default Thunderbird and Firefox versions.

If you want to keep Thunderbird and Firefox always in sync with the latest stable releases from Mozilla, then use the [Ubuntuzilla repository]("http://ubuntuzilla.wiki.sourceforge.net/") ([#2 in my tutorial]("http://lovinglinux.megabyet.net/?page_id=220##2---Automatic-installation-of-fresh-final-releases-from-Ubuntuzilla-3")). It will install the latest versions of both applications side-by-side with the default versions and will update them according to stable releases from Mozilla.

---

### Post by jimmyUT on 2010-02-02
thanks for the help

---

