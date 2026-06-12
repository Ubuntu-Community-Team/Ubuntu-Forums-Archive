---
title: "Flash and Youtube dont work."
date: 2009-11-05
forum: General Help
---

### Post by fbjoey on 2009-11-05
I'm running ubuntu on C Series Lifebook for a while and have never bean able to play flash games, see flash adverts or play videos clip on youtube  (I often get sound but the video freezes). 

Fbjoey

---

### Post by wrgb2 on 2009-11-05
Do you have flashplugin-nonfree installed?

---

### Post by XDevHald on 2009-11-05
Also goto [http://www.adobe.com/go/EN_US-H-GET-FLASH](http://www.adobe.com/go/EN_US-H-GET-FLASH) <--- Then click the drop down and choose your type of download, in this version I would highly recommend .deb as it does the install for you.

---

### Post by aysiu on 2009-11-05
**Step 1**
Close Firefox or whatever web browser you're using.

**Step 2**
Go to System > Administration > Synaptic Package Manager

**Step 3**
Search for *swfdec* and mark for removal anything in the search results that appears to be installed.

**Step 4**
Do the same for the term *gnash*

**Step 5**
Search for *flashplugin-nonfree* and mark that for installation

**Step 6**
Click **Apply**

**Step 7**
See if Flash is fixed.

---

### Post by XDevHald on 2009-11-05
You can do it this way as well, but does not reflect the installation of Flash being installed. You can simply install it without having to remove anything.

---

### Post by IBuntu.biz on 2009-11-05
apt-get install ubuntu-restricted-extras 

for MP3 playback, some other audio formats and GStreamer plugins, Microsoft fonts, Java runtime environment, Flash plugin, and DVD playback

good to have also (:

---

### Post by aysiu on 2009-11-05
> **XDevHald said:**
> You can do it this way as well, but does not reflect the installation of Flash being installed. You can simply install it without having to remove anything.
That's not true.

If the OP is experiencing Flash problems, it's very probable it is has to do with *swfdec* or *gnash* being installed, and even if you install the Adobe Flash, *swfdec* and *gnash* can interfere with the official Flash plugin and so should be removed.

---

### Post by aysiu on 2009-11-05
> **IBuntu.biz said:**
> apt-get install ubuntu-restricted-extras How about this instead? ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by fbjoey on 2009-11-05
I just installed it but still nothing works. 

An example would be Farmville on facebook. It open up the loading screen and just sits there and does nothing.

---

### Post by aysiu on 2009-11-05
> **fbjoey said:**
> I just installed it but still nothing works.  Did you remove *swfdec* and *gnash* too?

---

### Post by fbjoey on 2009-11-05
I went to remove them and it only gave the option of mark for install.

---

### Post by aysiu on 2009-11-05
> **fbjoey said:**
> I went to remove them and it only gave the option of mark for install.
Hm.

Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then post the output back here? ```
cat /etc/lsb-release
uname -a
dpkg -s mozilla-plugin-gnash
dpkg -s swfdec-mozilla
dpkg -s flashplugin-nonfree
ls -l /usr/bin/firefox
```

---

### Post by fbjoey on 2009-11-05
> fbjoey@Digger:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
fbjoey@Digger:~$ uname -a
Linux Digger 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/Linux
fbjoey@Digger:~$ dpkg -s mozilla-plugin-gnash
Package `mozilla-plugin-gnash' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
fbjoey@Digger:~$ dpkg -s swfdec-mozilla
Package: swfdec-mozilla
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 296
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 0.8.2-1ubuntu1
Replaces: swf-player
Provides: swf-player
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.1.3), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.14.0), liboil0.3 (>= 0.3.1), libpango1.0-0 (>= 1.22.0), libswfdec-0.8-0, zlib1g (>= 1:1.1.4)
Suggests: ubufox
Conflicts: swf-player
Description: Mozilla plugin for SWF files (Macromedia Flash)
 A GTK+ and swfdec based Mozilla plugin for SWF files,
 commonly known as Macromedia Flash animations.
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384,92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a,aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Description: GNOME SWF player ([http://swfdec.freedesktop.org/](http://swfdec.freedesktop.org/))
Npp-File: libswfdecmozilla.so
Npp-Mimetype: application/x-shockwave-flash, application/futuresplash
Npp-Name: Swfdec SWF player
Original-Maintainer: Santiago Garcia Mantinan <manty@debian.org>
fbjoey@Digger:~$ dpkg -s flashplugin-nonfree
Package: flashplugin-nonfree
Status: install ok installed
Priority: optional
Section: contrib/web
Installed-Size: 40
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 10.0.32.18ubuntu0.9.04.1
Depends: flashplugin-installer
Description: Adobe Flash Player plugin installer (transitional package)
 This package is a transitional package that can safely be removed after you installed
 flashplugin-installer.
Homepage: [http://wiki.ubuntu.com/FlashPlayer9](http://wiki.ubuntu.com/FlashPlayer9)
Original-Maintainer: Bart Martens <bartm@knars.be>
fbjoey@Digger:~$ ls -l /usr/bin/firefox


There you go :)

---

### Post by aysiu on 2009-11-05
So it looks as if even though swfdec isn't installed that *swfdec-mozilla* **is** installed.

So paste this command in to remove it: ```
sudo apt-get remove swfdec-mozilla
``` Then restart your web browser and see if you still have Flash problems.

---

### Post by fbjoey on 2009-11-05
:O It worked a treat. You're awesome. I'm having trouble playing DVD's as well. Can you help or should I post a new thread?

---

### Post by aysiu on 2009-11-05
> **fbjoey said:**
> :O It worked a treat. You're awesome. I'm having trouble playing DVD's as well. Can you help or should I post a new thread?
Post a new thread, and I'll try to help you out.

---

### Post by Oriol Gordó on 2009-11-15
I had the same problem than fbjoey. Thank you for your help!

---

