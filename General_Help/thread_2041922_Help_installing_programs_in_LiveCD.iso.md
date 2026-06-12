---
title: "Help installing programs in LiveCD.iso"
date: 2012-08-13
forum: General Help
---

### Post by Kopkins on 2012-08-13
Hello all, I've been trying to make a custom Ubuntu CD for a while now. After trying UCK several times, I'm moving back to the first thing I tried. I tried this a few times before, but was unsuccessful. This time, in 12.04.

[Here's the tutorial I've been using.]("https://help.ubuntu.com/community/LiveCDCustomization")

I get to the point where I'm installing software using apt-get. 
I do ```

apt-get update
add-apt-repository ppa:tualatrix/ppa
add apt-repository ppa:webupd8team/jupiter
apt-get update
apt-get install jupiter ubuntu-tweak
```Jupiter installs fine, but ubuntu-tweak fails with missing dependency error. Missing package python-compizconfig and cannot be installed.

I thought maybe if I upgrade everything I can get that package. 'apt-get upgrade' resulted in partial upgrade, then 'apt-get dist-upgrade' installed the 9 that were held back and 5 new. Nothing seemed too critical to what I was doing. Still couldn't get the package I needed. 

Additionally, updating seems to have left my iso unusable. Is it advisable not to upgrade during customization?

So I guess my question is, has anyone used this method successfully? It doesn't seem like it should be so complicated.

Thank you all,
Kopkins

---

### Post by Cheesehead on 2012-08-13
Do you have the Universe repo enabled?  Look in your chroot's /etc/apt/sources.list

What version of Ubuntu (11.04? 12,10?) are you trying to customize?

---

### Post by Kopkins on 2012-08-13
Universe was not enabled. I added ```
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe

``` will that do it?

I'm trying 12.04 precise.

Kopkins

EDIT: yes that did work, thank you. 

If I want to get files from my computer into the iso filesystem, how would I do that?

EDIT: Never mind, got it. Do the programs I install onto the livecd transfer into the installed system, so the actual users can use them?

---

### Post by Kopkins on 2012-08-14
So I finished an iso, but when I try to boot it, it hangs at the splash screen.

---

### Post by Kopkins on 2012-08-17
Does anyone have any suggestions? I really would like to get this working. 

Is it possible to create a bootable usb with persistence and install programs, then take the .iso from the usb and create a .iso image I can burn to a disk?

Kopkins

---

