---
title: "Adobe Flash plugin gray box (sound works)"
date: 2010-08-31
forum: General Help
---

### Post by gsedej on 2010-08-31
Hi,

I am using Ubuntu 10.04 (32bit) on Intel Atom / nvidia Ion computer.
Flash worked till last week, but I "suddenly" sterted getting **gray boxes** instead of flash content in **different browsers** (firefox, chromium). On Youtube, I can hear sound, so the video is playing but I only see gray box. I can pause/unpause by clicking on video, I can "extend" video by blind-clicking the right place. But if I (blindly) click on fullscreen, flashplugin.so crashes (ff and chromium).

I searched forums but problems were connected with 64bit or with gnash (I use 32 and adobe plugin).

I use adobe-flash 10.1. I tried all combinations (flashplugin-installer, .deb from adobe site) but never works. I always removed packages from synaptic before installing new one.
I do **not have installed** gnash or spark (nor swfdec).


So: flash plugin works odd in FireFox and Chromium. I can hear sound but picture is gray.

Is there anything else I can do?

Gašper

---

### Post by lovinglinux on 2010-08-31
See the third item at [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

---

### Post by gsedej on 2010-09-02
Hi, lovinglinux!

Thanks for reply.
Well, I don't see any flash content (only sound).
I done the 3. item but didn't work. I done hole procedure of 1. item, but don't work either.

I still wasn't able to set flash to work right. However I works ok in FF plugin called Cooliris.
Any other idea what can I do?
(I have similar configuration on other computers and works better)

Gašper

---

### Post by lovinglinux on 2010-09-02
> **gsedej said:**
> Hi, lovinglinux!

Thanks for reply.
Well, I don't see any flash content (only sound).
I done the 3. item but didn't work. I done hole procedure of 1. item, but don't work either.

I still wasn't able to set flash to work right. However I works ok in FF plugin called Cooliris.
Any other idea what can I do?
(I have similar configuration on other computers and works better)

Gašper

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

### Post by gsedej on 2010-09-02
Hi, lovinglinux

Thanks for reply!
Meanwhile I tested lightspark 0.4.4 and it at least showed the content but was slow and very unstable.

I reinstalled the flash-installer...

here is info

Shockwave Flash

    File: /usr/lib/flashplugin-installer/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r82

application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes


Firefox version 3.6.8
Mozzila FireFox for Ubuntu Canonical 1.0
nothing says about architecture... but it's ubuntu 10.04 32 bit on Intel Atom 1.6


report
```

Ubuntu Architecture

Linux seraph 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox						install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.8/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

...
only realative source is swiftfox

Flash packages

flashplugin-installer				install
flashplugin-nonfree				install

Plugin locations

/usr/lib/firefox-addons/plugins/libflashplayer.so
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

```


I hope it helps...

---

### Post by lovinglinux on 2010-09-02
> **gsedej said:**
> Hi, lovinglinux

Thanks for reply!
Meanwhile I tested lightspark 0.4.4 and it at least showed the content but was slow and very unstable.

I reinstalled the flash-installer...

here is info
I hope it helps...

Well, there is nothing wrong with your installation, so I would check for video driver issues. Also check if it works with a clean Firefox profile or with a new Ubuntu user account.

---

### Post by Vaphell on 2010-09-02
i recently rolled back to 64bit 10.0 flash despite it being vulnerable, wrapped 32 bit 10.1 annoyed me to no end
Missing video, unresponsive navigation in youtube clips (no way to get from the embedded clip to its youtube page or clip not starting at all), problems with z dimension (clicking some resolution option on youtube paused the clip because it registered a click on the video, not on the gui slapped on top of it)

---

### Post by gsedej on 2010-09-06
Hi,

I solved issue. Problem was with RGBA modules (B. Anderson ppa). I pure it and do some manuali downgradeing and now works ok.

Linux is not yet 100% perfect for rgba...

Thanks for your help!

---

### Post by stanca on 2010-09-06
I got the same problem for the last 2 months on x64 and x86 systems untill I found out that gtk2-module-rgba and gloobus-preview(who needs swfdec) don't work too well together with the flashplugin.;):)Now I'm using [Fake RGBA]("http://compiz-themes.org/content/show.php/Fake+RGBA+for+Compiz+Fusion+Color+Filter?content=94331").

---

### Post by gsedej on 2010-09-07
Hello again!

I solved issue. It was with ubuntu RGBA - transparency!!!
[https://wiki.ubuntu.com/DesktopTeam/RgbaGtkWithPPA/](https://wiki.ubuntu.com/DesktopTeam/RgbaGtkWithPPA/)

One of possibility is to purge RGBA libs to originals
```
sudo aptitude purge ppa:erik-b-andersen/rgba-gtk
```
And then remove source from repository.


Since you would perumably like to continue useing RGBA you need to change a file. There is file in home folder .profile (~/.profile)
you need to add folowing lines:
```

export GTK_MODULES=rgba
export GTK_RGBA_APPS=allbut:firefox-bin:gnome-mplayer:totem:openoffice:rhythmbox:chromium-browser:exe

```
the "exe" is for flash so it needs to be there!

AND LOGOUT! (necesseraly!)



...
well, I can't find out how to use on firefox, rgba can't detect program name
```
gasper@sirah:~$ firefox 
progname=<unknown>; RGBA=on
```

I will report if I will find out.

---

### Post by Tsu jan on 2010-09-18
I encountered this problem with Flash 10.1, FF 3.6.6 and RGBA module in Debian, a few months ago. It can be fixed without removing RGBA module by using "export XLIB_SKIP_ARGB_VISUALS=1" before Firefox command.

I always use the latest Firefox from the Mozilla site and just put "export XLIB_SKIP_ARGB_VISUALS=1" in the beginning of its SH file so that there's no need to change its command.

---

### Post by dpiekny on 2010-09-18
Thanks Tsu jan - this worked for me using a launcher with:

export XLIB_SKIP_ARGB_VISUALS=1 && firefox

---

### Post by Tsu jan on 2010-10-11
A better workaround is to add <unknown> to the exception list in '~/.profile' (see [http://www.madurax86.com/hrgbaflas/](http://www.madurax86.com/hrgbaflas/)). In this way, there would be no need to "export XLIB_SKIP_ARGB_VISUALS=1". BUT BE SURE TO PUT THE EXCEPTION LIST IN QUOTES, OTHERWISE THE GNOME SESSION WOULD NOT START! For example, use something like this (quoted from the above site):

export GTK_RGBA_APPS="allbut:firefox-bin:gnome-mplayer:totem:soffice:<unknown>:exe"

---

