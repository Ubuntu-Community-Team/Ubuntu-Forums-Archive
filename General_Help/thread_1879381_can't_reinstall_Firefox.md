---
title: "can't reinstall Firefox"
date: 2011-11-11
forum: General Help
---

### Post by eudeal on 2011-11-11
After apparently over tweaking 10.04 with Ubuntu Tweak my Firefox is gone. When attempting to re install I get the following message in the terminal:

The following packages have unmet dependencies:
  firefox: Depends: libasound2 (> 1.0.24.1)
           Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not installable
           Depends: libgtk2.0-0 (>= 2.24.0) but 2.20.1-0ubuntu2.1 is to be installed
           Depends: libstdc++6 (>= 4.6) but 4.4.3-4ubuntu5 is to be installed
           Recommends: firefox-globalmenu but it is not going to be installed

E: Broken packages

Any help on re installing Firefox will be greatly appreciated.
Thanks

Also when attempting re install via Synaptic Package Manager I get this error message when I select 'Firefox' for install.


firefox:
 Depends: libasound2 (> 1.0.24.1)
 Depends: libgdk-pixbuf2.0-0 (>=2.22.0) but it is not installable
  Depends: libgtk2.0-0 (>=2.24.0) but 2.20.1-0ubuntu2.1 is to be installed
  Depends: libstdc++6 (>=4.6) but 4.4.3-4ubuntu5 is to be installed
 Recommends: firefox-globalmenu but it is not going to be installed


Thanks again, any help will be greatly appreciated. I have searched forums and Googled the error messages but I always wind up with one of these error messages.

---

### Post by lovinglinux on 2011-11-11
Try to disable the mozilla-daily ppa added by Ubuntu Tweak, update, then try to install again.

---

### Post by eudeal on 2011-11-12
I purged 'Ubuntu Mozilla Daily Build Team PPA' in Tweak. The Software Center just spins when I select 'install' for Firefox and the Synaptic Package Manager still generates the same error message as before. Just noticed all of my Office.org apps are gone also. I really screwed the pooch with Tweak. Won't do that again. There are still more Firefox PPAs listed in Tweak. Should I purge them all?



Thanks

---

### Post by eudeal on 2011-11-12
Okay, disabled all Firefox related items. Synaptic Package Manager tries to install but generates this error message:

E: /var/cache/apt/archives/firefox_7.0.1+build1+nobinonly-0ubuntu0.10.04.1~mfs1_i386.deb: trying to overwrite '/usr/share/applications/firefox.desktop', which is also in package kubuntu-firefox-installer 

The Software Center just spins when I select 'install'. Can I just re install 10.04 without disturbing existing files and settings as one can with Windows?


Thanks

---

### Post by LinuxFan999 on 2011-11-12
> **eudeal said:**
> Okay, disabled all Firefox related items. Synaptic Package Manager tries to install but generates this error message:
 
E: /var/cache/apt/archives/firefox_7.0.1+build1+nobinonly-0ubuntu0.10.04.1~mfs1_i386.deb: trying to overwrite '/usr/share/applications/firefox.desktop', which is also in package kubuntu-firefox-installer 
 
The Software Center just spins when I select 'install'. **Can I just re install 10.04 without disturbing existing files and settings** as one can with Windows?
 
 
Thanks
Yes, but only if you have a separate home partition.

---

### Post by eudeal on 2011-11-12
Firefox installer appeared om my dock. When I attempt to install Firefox with it, I get the "Firefox installed' message then an error message stating that I have a broken package and to run 'apt-get install -f' in a terminal. When I do that Firefox installation is attempted unsuccessfully and ends with:

 Errors were encountered while processing:
 /var/cache/apt/archives/firefox_7.0.1+build1+nobinonly-0ubuntu0.10.04.1~mfs1_i386.deb


Any ideas what I should do? I have run 'repair broken packages' from the start up recovery menu several times to no avail. Again if I were sure I could re install 'Lucid' without disturbing files and apps I would. Any help is greatly appreciated.


Thanks

---

### Post by eudeal on 2011-11-12
Just saw response regarding 'separate home partition', I am running a dual boot system with Vista (albeit corrupt) on one partition and 10.4 on the other. I'm guessing that complicates things? Running aa MS/Linux dual boot has always been a 'trick of the wrist' for me. Windows does not like to play nice with any other OS and I have never been successful with WINE or Virtual Box. If I didn't have years of files on this PC I would just format and re install. Arrrrgh!!



Thanks

---

### Post by LinuxFan999 on 2011-11-12
> **eudeal said:**
> Just saw response regarding 'separate home partition', I am running a dual boot system with Vista (albeit corrupt) on one partition and 10.4 on the other. I'm guessing that complicates things? Running aa MS/Linux dual boot has always been a 'trick of the wrist' for me. Windows does not like to play nice with any other OS and I have never been successful with WINE or Virtual Box. **If I didn't have years of files on this PC I would just format and re install.** Arrrrgh!!
 
 
 
Thanks
If you have an external hard drive, you should back up your files before reinstalling Ubuntu.

---

### Post by eudeal on 2011-11-12
Thanks

---

### Post by lovinglinux on 2011-11-13
Try these:

```
sudo apt-get clean
sudo apt-get remove kubuntu-firefox-installer
sudo apt-get remove firefox
sudo apt-get update
sudo apt-get install firefox
```

---

