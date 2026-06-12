---
title: "Yet, more Flash problems."
date: 2010-08-07
forum: General Help
---

### Post by Zach G on 2010-08-07
This may seem redundant, but I'm having Flash Object problems, when I put my mouse over it, it seems to work fine, it'll highlight it or what knot, but when I click on it, no sound, or video. 

YouTube and Flash movies work fine (to get a better understanding of what I'm trying to do, go to [http://www.realmofdarkness.net]("http://www.realmofdarkness.net/"), and check out the "Soundboards" they're flash objects, they hardly work for me, the mouse will highlight it (But it will stop highlighting like every other second) but when I click on the object, it's unresponsive, no sound.

So is there currently a work around to get this to work? :-k:?

[Just checked, and flash games seem to be unresponsive too. :/]

---

### Post by flanagan on 2010-08-07
That site works for me under Firefox, using only the Adbobe flash plugin installed from [http://www.adobe.com](http://www.adobe.com). After installation, it shows up under Synaptic as *adobe-flashplugin* version 10.1.53.64-1lucid1.

---

### Post by Zach G on 2010-08-07
> **flanagan said:**
> That site works for me under Firefox, using only the Adbobe flash plugin installed from [http://www.adobe.com](http://www.adobe.com). After installation, it shows up under Synaptic as *adobe-flashplugin* version 10.1.53.64-1lucid1.

Did you use the soundboards on the site? The flash objects (and it just isn't this site alone) but when I click things they are either unresponsive or doing something weird, or not doing the right thing. YouTube works fine, ads seem to show up fine, but when I try to play a flash game, it's impossible..

---

### Post by lovinglinux on 2010-08-07
> **Zach G said:**
> Did you use the soundboards on the site? The flash objects (and it just isn't this site alone) but when I click things they are either unresponsive or doing something weird, or not doing the right thing. YouTube works fine, ads seem to show up fine, but when I try to play a flash game, it's impossible..

They work fine for me.

Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

If that doesn't work, then...

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://lh5.ggpht.com/_EPRFmO0pKhs/TFi0kGosJvI/AAAAAAAAAig/GNswcyQC75Y/s400/About_Plugins.jpg[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be locates at the bottom of the info dialog:

[IMG]http://lh5.ggpht.com/_EPRFmO0pKhs/TFi0kqRSPaI/AAAAAAAAAik/G3M3J5mmDOo/s400/Firefox_Version.jpg[/IMG]


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

### Post by ajgreeny on 2010-08-07
All work fine for me as well, so it is obviously something about your machine, or its setup, or the incorrect flash plugin(s) installed.

I have just the adobe-flashplugin from canonical partner repos, nothing else flash related, and flash works really well (for a linux operating system, anyway)

---

### Post by Zach G on 2010-08-07
> **lovinglinux said:**
> They work fine for me.

Get [FLASH-AID]("https://addons.mozilla.org/en-US/firefox/addon/161939/"), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

If that doesn't work, then..t[/CODE]


Okay, But first. It isn't just Firefox doing this, it also glitches/bugs up when I try to interact with desktop .SWF files. Flash-Aid helped, it'll actually interact with the soundboard but it wont generate audio when I click on it. 

Here's what you need (I think it's something in my audio settings for Flash? I don't know.)


[IMG]http://i857.photobucket.com/albums/ab131/Zach_G/Screenshot-1.png[/IMG]


[IMG]http://i857.photobucket.com/albums/ab131/Zach_G/Screenshot.png[/IMG]




And the "**Firefox-Report.txt**" 

[SIZE=1]Ubuntu Architecture

Linux ubuntu 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox                        install
firefox-branding                install
firefox-gnome-support                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.8/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

google-chrome.list
lucid-partner.list

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
[/SIZE]

---

### Post by Vaphell on 2010-08-07
don't you have gnash installed by any chance? if so, remove it.
you got way to many plugins with flash in name, especially when some of them are an alternative :)

---

### Post by Zach G on 2010-08-07
another weird thing is that, I just played a flash game, and it worked great. But the soundboards still aren't generating sound.. [The flash game/and youtube still is a little buggy]

---

### Post by Zach G on 2010-08-07
> **Vaphell said:**
> don't you have gnash installed by any chance? if so, remove it.
you got way to many plugins with flash in name, especially when some of them are an alternative 


yeah, I was having a problem with youtube before and had a bunch of flash players installed, but they're removed now. still no luck. But It's weird because, if I keep clicking around, he will say the lines, but I have to click rapidly and all over the place, so it's like all glitched up.

---

### Post by Zach G on 2010-08-07
Bump..  :frown:

---

### Post by lovinglinux on 2010-08-07
Looking at your report, I can't see anything wrong with your flash or Firefox installations, so I suspect it could be a pulseaudio issue. 

See [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html). There is a possible solution that deals with pulseaudio there.

It could be also an issue with 64bit. The site works for me, but I'm on 32bit right now.

---

### Post by Zach G on 2010-08-07
> **lovinglinux said:**
> Looking at your report, I can't see anything wrong with your flash or Firefox installations, so I suspect it could be a pulseaudio issue. 

See [Flash Issues & Solutions]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html"). There is a possible solution that deals with pulseaudio there.

It could be also an issue with 64bit. The site works for me, but I'm on 32bit right now.

Thank you so much!! I got it to work, I was running the 32bit plugin, and I edited it in terminal but forgot to put "export" 

gksudo gedit  /usr/lib/nspluginwrapper/i386/linux/npviewer

Then add the following line before the last line of that file:

[SIZE=3]**EXPORT**[/SIZE] GDK_NATIVE_WINDOWS=1



You're my hero. Next question, How do you reward people on here? :P

---

### Post by lovinglinux on 2010-08-07
> **Zach G said:**
> Thank you so much!! I got it to work, I was running the 32bit plugin, and I edited it in terminal but forgot to put "export" 

gksudo gedit  /usr/lib/nspluginwrapper/i386/linux/npviewer

Then add the following line before the last line of that file:

[SIZE=3]**EXPORT**[/SIZE] GDK_NATIVE_WINDOWS=1

You're my hero. Next question, How do you reward people on here? :P

You are welcome.

---

