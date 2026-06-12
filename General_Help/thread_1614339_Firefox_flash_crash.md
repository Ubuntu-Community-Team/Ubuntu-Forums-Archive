---
title: "Firefox flash crash"
date: 2010-11-05
forum: General Help
---

### Post by no1paladin on 2010-11-05
Hi, I am using firefox on ubuntu 10.04. And there is something wrong with my adobe flash plugin.

The symptom is as follows,
when I open a page of streaming media with flash, say a youtube page, it's working just fine. However, if I at the same time open new links or go forward/backward on other tabs, the page of the streaming media just crashes out sometimes, the part previously containing the flash  goes blank. 

The problem has bothered me for quite a while. I wonder if any friend here is familiar with this and can kindly offer a solution?

Thanks in advance!

---

### Post by silbak04 on 2010-11-05
Try installing the latest updated flashplayer [here]("http://get.adobe.com/flashplayer/") and then go ahead and move the .so file in your '.mozilla/firefox/plugins/' directory.

If you do not have a plugins directory, just create it in the firefox directory and stick the .so file in there, and restart firefox.

---

### Post by lovinglinux on 2010-11-05
Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by eoakes on 2010-11-06
:confused:
Thank you lovinglinux,

I did a clean istall of Ubuntu 10.10 on Oct. 16 and have accepted the updates offered since. I don't remember if Firefox was updated or not.

I noticed a few days ago that I was getting an error image in Firefox that said that Flash had crashed no report available.

Yesterday I started trying to fix it.

I did a scan in the Ubuntu Software Center and there as a program with a subtitle "Installer for the Adobe Flash Plugin for Mozilla". This was checked as installed. The Adobe Flash Plugin 10 was not checked as installed.

I installed Flash-AID and I still got the Flash error image.
[http://www.codegeek.net/flash-version.php](http://www.codegeek.net/flash-version.php) shows **" You have Flash player 10.1.102 installed."**

I tried un-installing and reinstalling FLASH_AID as I couldn't figure out how  make it run again.

Everything is still the same. Broken flash error image and the same installed plugins.

Is this a bug that I will have to wait for a system fix, or am I just missing something that needs to be installed or re-installed.

Thank you for any wisdom that you can provide,

Tom Oakes


**Shockwave Flash**

 File:  /usr/lib/flashplugin-installer/libflashplayer.soVersion:   Shockwave Flash 10.1 r102   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes  


Firefox version 3.6.12 Mozilla Firefox for Ubuntu Canonical-1.0

firefox-report.txt attached

Hardware:
# Intel Core 2 Duo Dual-Core E6300 2.8GHz 1066MHz 2MB Cache Processor

# ASRock G31M-S R2.0 Core 2 Quad/ Intel G31/ FSB 1600(OC)/ DDR2/ A&V&L/ 
MATX Motherboard

Display on motherboard interface

# 4GB (2X2GB) DDR2-1066 PC2 8500 Dual Channel

# Hitachi / WD 1TB 7200 RPM 32MB CACHE SATA 3.0Gb/s

---

### Post by lovinglinux on 2010-11-06
Your report shows your installation is fine.

You can run FLASH-AID from the extension button that should be placed on your toolbar. If not, then right-click on the toolbar, select customize, then drag the FLASH_AID icon to it. However, I doubt it will help, since everything that should be done by FLASH-AID has already been done.

You could try to start Firefox in safe mode or create a new profile to see if the problem persists. See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by no1paladin on 2010-11-07
Thanks so much for the detailed instruction. And excuse me for the late reply. Here is my output

> **lovinglinux said:**
> Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

**Shockwave Flash**

 File:  /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
Version:   
Shockwave Flash 10.1 r102 
  MIME Type Description Suffixes Enabled    
application/x-shockwave-flash Shockwave Flash swf Yes   
application/futuresplash FutureSplash Player spl Yes

**2 - Firefox version and architecture**

Firefox version 3.6.12 
Mozilla Firefox for Ubuntu canonical - 1.0


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

Ubuntu Architecture

Linux jasper-laptop 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox                        install
firefox-3.5                    install
firefox-3.5-branding                install
firefox-3.5-gnome-support            install
firefox-branding                install
firefox-gnome-support                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.12/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

google-talkplugin.list
karmic-partner.list
karmic-partner.list.distUpgrade

Flash packages

flashplugin-installer                install

Plugin locations

/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped

```

Does this look good?
Thanks

---

### Post by lovinglinux on 2010-11-08
> **no1paladin said:**
> Thanks so much for the detailed instruction. And excuse me for the late reply. Here is my output



Does this look good?
Thanks

Yes it looks good. Try to create a new Firefox profile and see if the problem persists.

---

