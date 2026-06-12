---
title: "Still'm having problems getting all flash video's to work..."
date: 2010-08-07
forum: General Help
---

### Post by michael.the.bone on 2010-08-07
I'm still unable to get all youtube videos working.

I've made all necessary changes from when flash didn't work last time.

I have both flash aid and flash video replacer,  however, some videos only load up and dont allow me to press play. When i right click on them, there is no flash options or information 

Also, it say's that i dont have flash player if i try to play anything  off myspace and when i have tried to download a flash packed it suggests  (both open and save as), it hasn't run...

Any ideas?

Cheers

---

### Post by Ginsu543 on 2010-08-07
Are you running a 64-bit OS? If so, this seems to be the same problem I used to have trying to run 32-bit Flash on a 64-bit system. Try this workaround:

1) Open Terminal
2) gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
3) Add before last line of file: export GDK_NATIVE_WINDOWS=1

It should look like:
```

#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer

```

---

### Post by dino99 on 2010-08-07
remove/purge (with synaptic) all related flash packages installed, then install flashplugin-installer (canonical partner repo need to be acivated into synaptic repo tab)

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

install gnome-codec-install and gnome-media

---

### Post by Nick_Jinn on 2010-08-07
I had problems when I had both the proprietary Macromedia flash codec as well as the open source one.....there are 3 choices. Just use one and stick with it. Try changing them around if one doesnt work, but dont use multiple at the same time. 

Are you using Medibuntu or just restricted extras?

I usually use Mint or Ubuntu Studio or Ultimate now and never have this problem.

---

### Post by michael.the.bone on 2010-08-07
> **Ginsu543 said:**
> Are you running a 64-bit OS? If so, this seems to be the same problem I used to have trying to run 32-bit Flash on a 64-bit system. Try this workaround:

1) Open Terminal
2) gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
3) Add before last line of file: export GDK_NATIVE_WINDOWS=1

[/CODE]

- I already had this line within the file?

**dino99**

-- I did a quick search in synaptic for "flash".  I only have;
flash plugin installer
kword
parley
restricted extras - highlighted, do i just need to remove the plugin installer? Or follow your steps with the terminal

**Nick_Jinn**

---I have the ubuntu-restricted extras highlighted, installed version 39

Mint or Ubuntu Studio or Ultimate - can these be used instead of flash? Do i get them in software centre?


Cheers for the reply's.

---

### Post by Nick_Jinn on 2010-08-07
The installer is not what you need. You need to install Macromedia Flash player, or one of the free alternatives.

Enanble third party and Multiverse in software sources and go to Synaptic and search for Flash. Some people prefer not using Macromedia flash codecs, but that is more of a philosophical issue or a development issue rather than an end user issue.


I would just install Medibuntu, the entire thing.

---

### Post by michael.the.bone on 2010-08-07
> **Nick_Jinn said:**
> The installer is not what you need. You need to install Macromedia Flash player, or one of the free alternatives.

Enanble third party and Multiverse in software sources and go to Synaptic and search for Flash. Some people prefer not using Macromedia flash codecs, but that is more of a philosophical issue or a development issue rather than an end user issue.


I would just install Medibuntu, the entire thing.



I just tired to download medibuntu from its suggested terminal code off the web site and got this message:


W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Also when i have to install marcomedia in different formats it comes up with an error..

Also, now youtube plays videos, only when they have fully loaded up...

Im very confused, im not sure what needs removing or adding or if the problem has been solved...

---

### Post by lovinglinux on 2010-08-07
FLASH-AID should have removed any conflicting plugins and installed the proper version from Adobe.

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

### Post by michael.the.bone on 2010-08-07
Ok so,

**1.** File:  /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
Version:Shockwave Flash 10.1 r53

**2.** Mine doesn't have this? It look exactly like yours but with out the bit you want...

**3.**
Ubuntu Architecture

Linux ubuntu 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

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

lucid-partner.list
medibuntu.list

Flash packages

flashplugin-installer				deinstall

Plugin locations

/usr/lib/firefox-addons/plugins/libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: broken symbolic link to `/usr/lib/mozilla/plugins/flashplugin-alternative.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

---

### Post by lovinglinux on 2010-08-07
> **michael.the.bone said:**
> 
Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: broken symbolic link to `/usr/lib/mozilla/plugins/flashplugin-alternative.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

Run FLASH-AID again to fix those errors. You can do that from the statusbar or the toolbar icons.

---

### Post by michael.the.bone on 2010-08-09
The Flash issue with myspace has been fixed. 

The you tube issue remains, however, i left the screen to load and i was able to play/pause and navigate through the video once it had fully loaded and started playing by itself...

Its not ideal, but if its best that can be achieve then it will have to do...

Thanks for the help again.

---

