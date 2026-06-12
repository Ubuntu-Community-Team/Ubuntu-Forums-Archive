---
title: "Baffled by the BBC (odd video problem)"
date: 2010-08-11
forum: General Help
---

### Post by dullard on 2010-08-11
Does anybody have an idea why video won't work for me in every installed browser on pages at [http://www.bbc.co.uk/news/](http://www.bbc.co.uk/news/) even though there's no problem at [http://www.bbc.co.uk/iplayer/](http://www.bbc.co.uk/iplayer/) ?

Originally I thought it was a Firefox problem and tried the usual fixes to no avail. Later I found that the problem exists in Chrome and Opera too.

UK user
Not using proxies
Ubuntu 8.04
Specific to BBC news video. No probs using youtube etc.

Help! :-)

---

### Post by dullard on 2010-08-11
The first frame appears briefly before the message appears as in the attached screenshot. Audio plays fine btw, but there's no play/pause control whatsoever.



Screengrab:

[http://img443.imageshack.us/img443/2614/screenshotbbcnewsamazon.png](http://img443.imageshack.us/img443/2614/screenshotbbcnewsamazon.png)

---

### Post by lovinglinux on 2010-08-12
Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog:

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

### Post by dullard on 2010-08-12
Okey dokey...

Flash path & version:

```
    File: /home/albert/.mozilla/plugins/libflashplayer.so
    Version: 
    Shockwave Flash 10.0 d20
```


Firefox version:

```
Mozilla/5.0 (X11; U; Linux x86_64; en-GB; rv:1.9.2.9pre) Gecko/20100811 Firefox/8.04 (hardy) Namoroka/3.6.9pre
```


firefox-report.txt:

```
Ubuntu Architecture

Linux albert-laptop 2.6.24-28-generic #1 SMP Sat Jul 31 18:10:55 UTC 2010 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.4 LTS"

Firefox Packages

firefox                        install
firefox-3.0                    install
firefox-3.0-gnome-support            install
firefox-3.5-gnome-support            install
firefox-branding                install
firefox-gnome-support                install
firefox32                    install
ia32-lib-firefox                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.9pre/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

google-chrome.list
m-buck-ppa.list
m-buck-ppa.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
opera.list
winff.list
winff.list.save

Flash packages


Plugin locations

/home/albert/.fr-6uZr53/install_flash_player_10_linux/libflashplayer.so
/home/albert/.mozilla/plugins/libflashplayer.so
/opt/swiftfox/plugins/libflashplayer.so
/opt/swiftfox/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
/usr/lib32/firefox32/plugins/libflashplayer.so
/usr/local/firefox32/plugins/libflashplayer.so


Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/libflashplayer.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
```

Cheers!

---

### Post by lovinglinux on 2010-08-12
The problem is that you only have, what appears to be an old 64bit version, manually installed under your Firefox profile directory. Adobe is no longer releasing a 64bit version, so your only option is to install the 32bit version from the repositories.

Since the version of the repositories for Ubuntu 8.04 is old, it probably won't work with those sites. 

I this case, you could try to download the most recent 32bit version from Adobe and manually replace the version from the repositories.

Install and run [FLASH-AID]("https://addons.mozilla.org/en-US/firefox/addon/161939/") to remove the current plugin and install the one from the repositories.

Then [download version 10]("http://get.adobe.com/flashplayer/") tar file for 32bit from Adobe and extract the **libflashplayer.so** to **/usr/lib/flashplugin-installer/**, thus replacing the current version located on that folder. I'm not sure this will work tho.

---

### Post by chiossif on 2010-08-13
Hi to all.

I've got two PCs both with Lucid AMD64.

PC #1 plays all videos on ff. It's data are:

```

Shockwave Flash

    File: /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r82

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.8) Gecko/20100723 Ubuntu/10.04 (lucid) Firefox/3.6.8

Ubuntu Architecture

Linux DELL-D830 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

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

gnuzilla-team-ppa-lucid.list
gnuzilla-team-ppa-lucid.list.save
google-chrome.list
google-chrome.list.save
medibuntu.list
medibuntu.list.save

Flash packages

flashplugin-installer				install

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

PC #2 plays all youtube videos BUT not a few from other sites (even those embedded from youtube). #2 data are: 

```

Shockwave Flash

    File: /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r82

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.8) Gecko/20100723 Ubuntu/10.04 (lucid) Firefox/3.6.8

Ubuntu Architecture

Linux chiossif-6400 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

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

dropbox.list
dropbox.list.save
gnuzilla-team-ppa-lucid.list
gnuzilla-team-ppa-lucid.list.save
google-chrome.list
google-chrome.list.save
medibuntu.list
medibuntu.list.save
opera.list
opera.list.save

Flash packages

flashplugin-installer				install

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

I can see no difference at all.
BUT PC #2 cannot play ALL videos :-(
Obviously there is a difference somewhere :-/

Can you help me? 

(Additional info:

PC #1 has an NVIDIA with proprietary driver:
```
 
01:00.0 VGA compatible controller [0300]: nVidia Corporation Quadro NVS 140M [10de:0429] (rev a1)

``` 

while PC #2 an ATI with open source:
```
 
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV530LE [Radeon X1600/X1650 PRO] [1002:71c6]

``` 

What do you think ? :-/ )

Thanks :-)

---

### Post by lovinglinux on 2010-08-13
> **chiossif said:**
> 
I can see no difference at all.
BUT PC #2 cannot play ALL videos :-(
Obviously there is a difference somewhere :-/

Can you help me? 

What do you think ? :-/ )

Thanks :-)


Indeed there is no difference and everything looks like it should be. Try to enable third-party cookies in Firefox. Some users have an issue with embedded videos from YouTube. Enabling third-party cookies should fix it. If not, then see Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by chiossif on 2010-08-13
> **lovinglinux said:**
> Indeed there is no difference and everything looks like it should be. Try to enable third-party cookies in Firefox. Some users have an issue with embedded videos from YouTube. Enabling third-party cookies should fix it. If not, then see Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

Thanks for your immediate reply. On #2 I've installed and tested for this problem Chrome, IceCat, Seamonkey and Opera. ALL browsers have the same problems: while ALL pass Adobe's flash test and play youtube videos, they have a blank screen on others :-(

The only think I haven't done is to test on a new user account...
I'll be back if this is the case...

---

### Post by chiossif on 2010-08-13
> **chiossif said:**
> ...

The only think I haven't done is to test on a new user account...
I'll be back if this is the case...

IT IS.

I've just cleared my home account:
```

  494  cd ~
  495  rm -R .mozilla
  496  rm -R .adobe/
  497  rm -R .mplayer/
  498  rm -R .macromedia/
  499  rm -R .icedteaplugin
  500  history
```
 (after a bookmarks backup :-) ) and everything works like a charm :-)

Thanks for the support :-)

---

### Post by lovinglinux on 2010-08-13
> **chiossif said:**
> IT IS.

I've just cleared my home account:
```

  494  cd ~
  495  rm -R .mozilla
  496  rm -R .adobe/
  497  rm -R .mplayer/
  498  rm -R .macromedia/
  499  rm -R .icedteaplugin
  500  history
```
 (after a bookmarks backup :-) ) and everything works like a charm :-)

Thanks for the support :-)

You are welcome.

---

### Post by nicksanders on 2010-10-11
I've had the same problem, its been bugging me for ages, thanks for solving it.

FYI all I needed was rm -fr ~/.macromedia

---

