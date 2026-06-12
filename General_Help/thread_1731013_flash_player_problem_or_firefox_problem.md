---
title: "flash player problem or firefox problem?"
date: 2011-04-16
forum: General Help
---

### Post by zdarova on 2011-04-16
I tried to install 10.10 32bit on my desktop, I wasn't able to finish the install, maybe because of the chipset/GPU, it gave me "white line" and the flashing the screen, finaly I was able to boot without graphics and reinstalled only the base repertories. Also firefox as root. 

After I was able to boot in graphic mode and have a "normal ubuntu installation", in Gnome firefox was not starting. Later I figured up that was the root problem, because from terminal with sudo firefox worked. 
I changed some rights rule and now this works.

But I still have problems with the flash plugin, I am not able to play any flash, about:plugins in firefox said that: No plugins instaled, I tried to install flash from firefox bar aslo from Adobe website and nothing :confused: 

I removed also the Gnash plugin and still not works. 

I think the problem is because I installed firefox in root and now the plugins are in a different folder, but I don't know how to fix that...


EDIT: I am adding the report from Flash Aid plug in:
```
Ubuntu Architecture

Linux ubuntu 2.6.35-28-generic-pae #50-Ubuntu SMP Fri Mar 18 20:43:15 UTC 2011 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox						install
firefox-branding				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.16/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources


Flash packages

flashplugin-installer				install
Plugin locations

/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks


/usr/lib/mozilla/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/mozilla/plugins/libflashplayer.so' (Permission denied)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (Permission denied)
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'
/usr/lib/flashplugin-installer/libflashplayer.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory)
/usr/lib/adobe-flashplugin/libflashplayer.so: ERROR: cannot open `/usr/lib/adobe-flashplugin/libflashplayer.so' (No such file or directory)
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory)
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory)
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)

pluginreg.dat


```

---

### Post by lovinglinux on 2011-04-16
Well, starting Firefox with sudo cause problems with your profile. I suppose you have already changed the ownership of your mozilla folder and sub folders. Check if you are really the owner of your profile at ~/.mozilla/firefox. If you are, then try deleting the file pluginreg.dat, which seems to be empty and could be causing the problem.

Also, try running Flash-Aid again. I am not sure if you have already done that, because by default flash-Aid install the beta version of flash and you have the one from the repositories.

---

### Post by zdarova on 2011-04-18
I checked if the permission in ~/.mozilla/firefox are mine, and there compares my user name...but i did not found any pluginreg.dat fine to delete...:(

I tried again to run Flash Aid, first "execute", restart firefox, then "test"...and the problem remains...:confused:

EDIT: this is the output of shell when I press Execute on Flash Aid:
```
2011-04-18 13:07:20 (113 KB/s) - `flashplayer32' saved [5537060/5537060]

libflashplayer.so
usr/
usr/bin/
usr/bin/flash-player-properties
usr/share/
usr/share/kde4/
usr/share/kde4/services/
usr/share/kde4/services/kcm_adobe_flash_player.desktop
usr/share/applications/
usr/share/applications/flash-player-properties.desktop
usr/share/icons/
usr/share/icons/hicolor/
usr/share/icons/hicolor/22x22/
usr/share/icons/hicolor/22x22/apps/
usr/share/icons/hicolor/22x22/apps/flash-player-properties.png
usr/share/icons/hicolor/48x48/
usr/share/icons/hicolor/48x48/apps/
usr/share/icons/hicolor/48x48/apps/flash-player-properties.png
usr/share/icons/hicolor/24x24/
usr/share/icons/hicolor/24x24/apps/
usr/share/icons/hicolor/24x24/apps/flash-player-properties.png
usr/share/icons/hicolor/32x32/
usr/share/icons/hicolor/32x32/apps/
usr/share/icons/hicolor/32x32/apps/flash-player-properties.png
usr/share/icons/hicolor/16x16/
usr/share/icons/hicolor/16x16/apps/
usr/share/icons/hicolor/16x16/apps/flash-player-properties.png
usr/lib/
usr/lib/kde4/
usr/lib/kde4/kcm_adobe_flash_player.so
[sudo] password for zdarova: 
ln: creating symbolic link `/usr/lib/firefox-addons/plugins/libflashplayer.so': File exists

```

---

### Post by lovinglinux on 2011-04-18
> **zdarova said:**
> I checked if the permission in ~/.mozilla/firefox are mine, and there compares my user name...but i did not found any pluginreg.dat fine to delete...:(


The pluginreg.dat is inside ~/.mozilla/firefox/<profilename>/

However, it seems it is not created yet. Open Firefox Add-ons Manager abd check if the plugins are there.

> **zdarova said:**
> 
I tried again to run Flash Aid, first "execute", restart firefox, then "test"...and the problem remains...:confused:

EDIT: this is the output of shell when I press Execute on Flash Aid:


The output is okay.

---

### Post by zdarova on 2011-04-18
I found the problem, it was because the plugin wanted sudo mode: 
entering in firefox by console: sudo firefox, flash was working. 

So I created a folder in usr/lib/firefox/plugins, pasted there libflashplayer.so, used some command with Chmod 777 for this file and now works also when I open Firefox normaly :) 

thanks for the help!

---

### Post by lovinglinux on 2011-04-18
> **zdarova said:**
> I found the problem, it was because the plugin wanted sudo mode: 
entering in firefox by console: sudo firefox, flash was working. 

So I created a folder in usr/lib/firefox/plugins, pasted there libflashplayer.so, used some command with Chmod 777 for this file and now works also when I open Firefox normaly :) 

thanks for the help!

Never use *sudo* with Firefox. If you did it again, then you messed with your profile again.

If you ever need to start Firefox with root privileges, which I strongly not recommend, then use *gksudo* instead.

---

### Post by zdarova on 2011-04-18
> **lovinglinux said:**
> Never use *sudo* with Firefox. If you did it again, then you messed with your profile again.

If you ever need to start Firefox with root privileges, which I strongly not recommend, then use *gksudo* instead.
ok, thanks

---

