---
title: "Need Two Firefox Versions"
date: 2011-04-29
forum: General Help
---

### Post by wadedesk on 2011-04-29
I just upgraded to Ubuntu 11.04.  HATE new desktop, so running Classic mode.  Upgrade included Firefox 4.0 which is great for web surfing, but I need to also run Firefox 3.6 so that I can continue to use several dozen Prism Web Apps.  

Is it possible to do a custom install of Firefox 3.6 to regain Prism support (without removing 4.0)?  In Windows, I used a Portable version of 3.6 to run Prism and the installed version of 4.0 for general surfing.  However, I don't like the rendering of Firefox Portable in Wine.

I'm not a happy camper that Prism support was ended, as Chrome does not do the job that Prism did.  Consequently, I would like to run Firefos 3.6 until there is a better alternative.

Can anyone give me detailed instructions for maintaining two versions of Firefox in Ubuntu?

---

### Post by lovinglinux on 2011-04-30
You can easily download, extract and run any version of Firefox distributed by Mozilla. See method #2 of [http://www.webgapps.org/firefox/installing-other-versions](http://www.webgapps.org/firefox/installing-other-versions)

However, you will need to setup a different profile and start Firefox with the *[-no-remote]("http://www.webgapps.org/master/tutorials/firefox/general/profiles-and-backups")* option, if you want to run both simultaneously.

To manage multiple profiles and versions, I recommend using the new [Mozilla's Profile Manager]("https://developer.mozilla.org/en/Profile_Manager").

---

### Post by wadedesk on 2011-04-30
I was able to download Firefox 3.6 and extract the files in my Home folder.  I was able to reinstall the Prism Plug-in, but had to recreate all my 83 Prism web apps since they were tied to a Prism application that was deleted during upgrade.  Since Prism runs as a seperate application, I do not have to use Session Manager in order to run Prism web apps using the 3.6 engine and Firefox 4.0.

It appears that Firefox 3.6 launched from my Home folder uses the Plug-in, Bookrmark, even open Tabs from Firefox 4.0.  I do not know that this will create any issues since I only open FF 3.6 to create a Prism app and then launch it from the icon there after.

One problem that I have is that Prism (Firefox 3.6) needs Adobe Flash Player installed.  I'm running Ubuntu 64-bit, so I can not install the latest 32-bit DEB version from the Adobe web site.  I am hesitant to download the 64-bit beta version from Adobe since it may conflict with the existing app already installed.

Anyone have any ideas on how to get Adobe Flash Player installed in my Firefox 3.6 / Prism application?

---

### Post by lovinglinux on 2011-04-30
> **wadedesk said:**
> It appears that Firefox 3.6 launched from my Home folder uses the Plug-in, Bookrmark, even open Tabs from Firefox 4.0.  I do not know that this will create any issues since I only open FF 3.6 to create a Prism app and then launch it from the icon there after.

I don't recommend using the same profile with two different versions on a daily basis. That's why I recommended that you use the [Profile Manager]("https://developer.mozilla.org/en/Profile_Manager"). Instead of launching Firefox from the default Ubuntu launcher, you will launch it from the profile manager, which allows to choose the profile and version.

> **wadedesk said:**
> One problem that I have is that Prism (Firefox 3.6) needs Adobe Flash Player installed.  I'm running Ubuntu 64-bit, so I can not install the latest 32-bit DEB version from the Adobe web site.  I am hesitant to download the 64-bit beta version from Adobe since it may conflict with the existing app already installed.

Anyone have any ideas on how to get Adobe Flash Player installed in my Firefox 3.6 / Prism application?

Make sure both Firefox versions are 64bit, then install and execute my [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") extension on the default Firefox. Don't need to install on both, although it won't hurt to do so.

When executed, [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") detects your browser architecture and installs the latest beta flash 64bit.

Keep in mind that you need to create a symlink to the plugin folder for the Firefox installed manually. If you followed all the instructions in my tutorial, you already have that. Let me know if it doesn't work.

On a side note, Prism is a dead project and is no longer being developed, so I wouldn't depend much on it if you want to keep you web apps compatible in the future. Read [this]("https://wiki.mozilla.org/Prism") for alternatives.

---

### Post by wadedesk on 2011-05-02
When I go to Mozilla releases download, I do not see an option to download 32-bit or 64-bit versions.  However I did install Flash-Aid in Mozilla 3.6.17.  It reports that I'm running 64-bit, but that I have a 32-bit version of Adobe Flash installed.  I also see where a 32-bit tweaking program installed.

Here is a report that I generated:

[PHP]Flash packages

Plugin locations

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/mozilla/plugins/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory)
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory)
/usr/lib/adobe-flashplugin/libflashplayer.so: ERROR: cannot open `/usr/lib/adobe-flashplugin/libflashplayer.so' (No such file or directory)
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory)
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory)
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)[/PHP]

Apparently my system needs some help and I'm not sure how to proceed.

---

### Post by lovinglinux on 2011-05-02
> **wadedesk said:**
> When I go to Mozilla releases download, I do not see an option to download 32-bit or 64-bit versions.  However I did install Flash-Aid in Mozilla 3.6.17.  It reports that I'm running 64-bit, but that I have a 32-bit version of Adobe Flash installed.  I also see where a 32-bit tweaking program installed.

Here is a report that I generated:

[PHP]Flash packages

Plugin locations

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/mozilla/plugins/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory)
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory)
/usr/lib/adobe-flashplugin/libflashplayer.so: ERROR: cannot open `/usr/lib/adobe-flashplugin/libflashplayer.so' (No such file or directory)
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory)
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory)
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)[/PHP]

Apparently my system needs some help and I'm not sure how to proceed.

According to your report, you are already running flash 64bit.

You can get Firefox 64bit from the [nightly repository]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-firefox-3.6.x/").

---

### Post by wadedesk on 2011-05-03
Downloading the (last) nightly build of Firefox 3.6.x for 64-bit OS worked.  Prism works perfectly with Adobe Flash Player.  I'm very pleased that I will be able to continue to use Prism on Ubuntu 11.04 64-bit until a better web app appears.  Prism allows me to login to one web account while logged into another account on the same site.  Chrome does not allow use of different IDs on the same server.

---

