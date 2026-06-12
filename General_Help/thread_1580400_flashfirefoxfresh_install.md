---
title: "flash/firefox/fresh install"
date: 2010-09-23
forum: General Help
---

### Post by osmorphyus on 2010-09-23
platform: karmic, 9.10

issue:  when trying to take a picture with my webcam via flash in a web page, the flash applet never displays.

is this due to the java package not being installed by default?  i am installing the ubu restricted extras, will this correct this problem?

p.s.
-if i could upload a pic to the forum to show what its doing i would be most gracious.
[IMG]file:///home/death/Desktop/Screenshot.png[/IMG]

---

### Post by pedro_orange on 2010-09-23
The meta-package 'ubuntu-restricted-extras' contains both Java and Flash. 
If you are trying to use applications that utilize either of these technologies, you should get them installed before trying to use them anymore.

---

### Post by osmorphyus on 2010-09-23
alright, rest-extras just finished downloading/installing and i still cant use the webcam feature of flash, the applet never even loads.

any help is appreciated.

---

### Post by pedro_orange on 2010-09-23
I don't know what website you're trying to get to. So I can't comment from that site if it works or not. (I don't even have a WebCam!)

However, does your WebCam work in Linux? 
Please see: [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

You might need to install something. This is a good resource for that.

---

### Post by osmorphyus on 2010-09-23
anyone else can feel free to jump into this.  the webcam is supported, flash does not seem to be fully or properly installed, or maybe it comes down to java.

i downloaded the restr-extras pack, rebooted, still no dice.  come on gang, any help is appreciated.

---

### Post by osmorphyus on 2010-09-23
issue is still open.  help!

---

### Post by PRC09 on 2010-09-23
You could try the following for troubles with Flash.lovinglinux is usually around this board fairly often.....

[http://flash-aid-extension.blogspot.com/](http://flash-aid-extension.blogspot.com/)

---

### Post by lovinglinux on 2010-09-24
> **PRC09 said:**
> You could try the following for troubles with Flash.lovinglinux is usually around this board fairly often.....

[http://flash-aid-extension.blogspot.com/](http://flash-aid-extension.blogspot.com/)

Unfortunately, I have no experience with web cams, but flash-aid indeed should help.

---

### Post by osmorphyus on 2010-09-24
flash aid didnt rectify this problem, firefox still tells me there are missing plugins when i go to the test flash page (adobe).

i click to install missing plugins and firefox comes back with nothing is available.

is there any other browser that works 100% right now?  in XP i had some missing plugins issues with firefox, and firefox kept installing flash 10 oveeer and ovbvver again in XP.


any browser out right now with 100% working flash functionality?  for ubu?

---

### Post by lovinglinux on 2010-09-24
> **osmorphyus said:**
> flash aid didnt rectify this problem, firefox still tells me there are missing plugins when i go to the test flash page (adobe).?

Has FLASH-AID executed a bunch of commands in a terminal? Have you  restarted Firefox after running FLASH-AID?

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

### Post by osmorphyus on 2010-09-24
**Has FLASH-AID executed a bunch of commands in a terminal? Have you  restarted Firefox after running FLASH-AID?**

- yes executed commands/rebooted.

[B]plugin.expose_full_path
was set to false, now is true.
  
  

[/B]**Shockwave Flash**

 File:  /usr/lib/flashplugin-installer/libflashplayer.soVersion:   Shockwave Flash 10.1 r85   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes



FIREFOX V 3.6.10
MOZ..  ff FOR UBUNTU, CANONI... -1.0

**Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.10) Gecko/20100915 Ubuntu/9.10 (karmic) Firefox/3.6.10**







_***results of commands in terminal:***_
Ubuntu Architecture

Linux death-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

Firefox Packages

firefox                        install
firefox-3.5                    deinstall
firefox-3.5-branding                install
firefox-3.5-gnome-support            install
firefox-branding                install
firefox-gnome-support                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.10/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources


Flash packages

flashplugin-installer                install
flashplugin-nonfree                install

Plugin locations

/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/flashplugin-alternative.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

---

### Post by lovinglinux on 2010-09-24
Everything is normal in your setup. Do you get the error when visiting YouTube?

---

### Post by B Crowther on 2010-09-27
I have never heard of FLASH-AID before: realised today that Shockwave was no longer happening since Update Manager installed FF 3.6.10, surfed around to this thread, installed FLASH-AID, hit the tit, and all is now good.

I like!:)

Regards,
Bruce

---

### Post by lovinglinux on 2010-09-28
> **B Crowther said:**
> I have never heard of FLASH-AID before: realised today that Shockwave was no longer happening since Update Manager installed FF 3.6.10, surfed around to this thread, installed FLASH-AID, hit the tit, and all is now good.

I like!:)

Regards,
Bruce

I'm glad you liked it. I'm the developer btw. ;)

---

### Post by borth92 on 2010-09-28
if your running 64-bit, you need to insert the beta 64-bit flash from Adobe Labs to home/.mozilla/plugins

---

### Post by lovinglinux on 2010-09-28
> **borth92 said:**
> if your running 64-bit, you need to insert the beta 64-bit flash from Adobe Labs to home/.mozilla/plugins

FLASH-AID supports the new 64bit and extracts it to system folder, so it can be used by all accounts.

---

