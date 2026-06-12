---
title: "Updating Firefox"
date: 2010-02-20
forum: General Help
---

### Post by Ibrahim mufeed on 2010-02-20
Hi guys,

I am using Ubuntu 9.10, and I do not do update my packages when it ask me for, since I am afraid of changing the start-up boot menu after updating the linux kernel, and also I think it is not important to update software packages.

Recently [month ago] I checked the FIREFOX check boxes ONLY and run the update. After that step what I got was something new called [Namoroka] which a development version of Firefox, All what I need now is to switch to latest version of Firefox 3.6.

There is no check for update option under Help. Any idea?? I will be thankful.

---

### Post by SuperSonic4 on 2010-02-20
Namoroka *is* the latest version of firefox

---

### Post by spiky001 on 2010-02-20
is Namoroka not the 3.6 version? Shiretoko was 3.5

---

### Post by Ibrahim mufeed on 2010-02-20
It is version 3.6.1pre.

---

### Post by jsriz on 2010-02-20
> **Ibrahim mufeed said:**
>  I got was something new called [Namoroka] which a development version  of Firefox.
hence you will not find it in synaptic.
Go to the site with your old browser it will show steps to upgrade.
Else download the source code on the site
Extract it and 
Run the firefox script.
To make launching easy You can create a launcher for this script on desktop and give it the icon of fireox (in the icons folder)

---

### Post by Tibuda on 2010-02-20
To always have the latest Firefox in Ubuntu, I recommend you to use the Ubuntuzilla repository. Instructions here: [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation)
(it only works in x86, because Mozilla does not release 64bits binaries)

---

### Post by lovinglinux on 2010-02-20
See the [COLOR="Sienna"]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by northd_tech on 2010-02-20
When I use the Firefox 3.6 link here:

[http://www.mozilla.com/products/download.html?product=firefox-3.6&os=linux&lang=en-US](http://www.mozilla.com/products/download.html?product=firefox-3.6&os=linux&lang=en-US)

[http://www.mozilla.com/en-US/firefox/upgrade.html](http://www.mozilla.com/en-US/firefox/upgrade.html)

I am able to download file "firefox-3.6.tar.bz2" and extract it to a subdirectory on the Desktop.

When I run the firefox script I get this:

sudo sh ./firefox

> /usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.soWhen I tried it the first time, I saw this:

> Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
Then I get a dialog message about Firefox already running.  When I view Help > About Mozilla Firefox, it shows version 3.0.18.

The "Check for Updates" is grayed out, and both Firefox 3.0 and 3.5 show to be installed under Synaptic Package Manager.

I've been having some slow internet (IPv6, OpenDNS type ) issues and was hoping that updating Firefox might help.  I'm running a 64-bit dual processor AMD under 64-bit Jaunty 9.04 and a 2.6.28-18-generic kernel.

Is version 3.0.18 as new as I can run with the 64-bit thing, or does anyone know how to get this to update?

I'll need to close out my browser to attempt running the script again, but I might be able to get back here under Konqueror.

---

### Post by northd_tech on 2010-02-20
Weird- it worked that 3rd time after throwing all these messages and it shows to be ver 3.6 now.

>  
FoxyProxy settingsDir: /home/xxxxxxx/.mozilla/firefox/d08cxfhj.default/foxyproxy.xml
LoadPlugin: failed to initialize shared library /usr/lib/swfdec-mozilla/libswfdecmozilla.so [/usr/lib/swfdec-mozilla/libswfdecmozilla.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so [/usr/lib/mozilla/plugins/mplayerplug-in-dvx.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/mplayerplug-in-qt.so [/usr/lib/mozilla/plugins/mplayerplug-in-qt.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/mplayerplug-in-rm.so [/usr/lib/mozilla/plugins/mplayerplug-in-rm.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so [/usr/lib/mozilla/plugins/mplayerplug-in-wmp.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/mplayerplug-in.so [/usr/lib/mozilla/plugins/mplayerplug-in.so: wrong ELF class: ELFCLASS64]
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
I'm guessing it must be something to do with incompatible plugins.

edit:  It took some messing around and several restarts in order to get the Launcher and icon straightened out- is there an easier way to fix all that?

---

### Post by lovinglinux on 2010-02-20
> **northd_tech said:**
> When I use the Firefox 3.6 link here:

[http://www.mozilla.com/products/download.html?product=firefox-3.6&os=linux&lang=en-US](http://www.mozilla.com/products/download.html?product=firefox-3.6&os=linux&lang=en-US)

[http://www.mozilla.com/en-US/firefox/upgrade.html](http://www.mozilla.com/en-US/firefox/upgrade.html)

I am able to download file "firefox-3.6.tar.bz2" and extract it to a subdirectory on the Desktop.

When I run the firefox script I get this:

sudo sh ./firefox

When I tried it the first time, I saw this:

Then I get a dialog message about Firefox already running.  When I view Help > About Mozilla Firefox, it shows version 3.0.18.

The "Check for Updates" is grayed out, and both Firefox 3.0 and 3.5 show to be installed under Synaptic Package Manager.

I've been having some slow internet (IPv6, OpenDNS type ) issues and was hoping that updating Firefox might help.  I'm running a 64-bit dual processor AMD under 64-bit Jaunty 9.04 and a 2.6.28-18-generic kernel.

Is version 3.0.18 as new as I can run with the 64-bit thing, or does anyone know how to get this to update?

I'll need to close out my browser to attempt running the script again, but I might be able to get back here under Konqueror.

> **northd_tech said:**
> Weird- it worked that 3rd time after throwing all these messages and it shows to be ver 3.6 now.

I'm guessing it must be something to do with incompatible plugins.

edit:  It took some messing around and several restarts in order to get the Launcher and icon straightened out- is there an easier way to fix all that?


I don't know where did you get the information that you should run it with **sudo sh ./firefox**. The file you have downloaded is a ready-to-run binary, which means you just need to extract it and run the firefox file inside the extracted firefox folder. Additionally, **NEVER** run firefox with *sudo*. See [this](http://lovinglinux.megabyet.net/?page_id=220#Firefox-doesn%27t-start-through-regular-command/menu-but-starts-using-%22sudo-firefox%22--2) to fix the problems you have created by doing that.

Since you are running 64bit Ubuntu I would recommend that you delete the firefox folder that you have extracted to your Desktop, apply the ownership fix from the previous link, than add the **mozillateam/firefox-stable** ppa and update your system. Firefox will be upgraded to 3.6 64bit version. See [this](http://lovinglinux.megabyet.net/?page_id=220##3---Installation-from-PPA-repositories-3) for additional instructions.

---

### Post by northd_tech on 2010-02-21
> **lovinglinux said:**
> I don't know where did you get the information that you should run it with **sudo sh ./firefox**. The file you have downloaded is a ready-to-run binary, which means you just need to extract it and run the firefox file inside the extracted firefox folder. Additionally, **NEVER** run firefox with *sudo*. See [this]("http://lovinglinux.megabyet.net/?page_id=220#Firefox-doesn%27t-start-through-regular-command/menu-but-starts-using-%22sudo-firefox%22--2") to fix the problems you have created by doing that.

Since you are running 64bit Ubuntu I would recommend that you delete the firefox folder that you have extracted to your Desktop, apply the ownership fix from the previous link, than add the **mozillateam/firefox-stable** ppa and update your system. Firefox will be upgraded to 3.6 64bit version. See [this]("http://lovinglinux.megabyet.net/?page_id=220##3---Installation-from-PPA-repositories-3") for additional instructions.
Actually, the ownership/permissions weren't changed and didn't need to be fixed- I was still the owner of everything under ~/.mozilla/ (including the /firefox/ and /extensions/ directories and their contents).

Your 64-bit link:

[http://lovinglinux.megabyet.net/?page_id=220##3---Installation-from-PPA-repositories-3](http://lovinglinux.megabyet.net/?page_id=220##3---Installation-from-PPA-repositories-3)

links here:

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

which links here for Jaunty 9.04:

[https://edge.launchpad.net/+help/soyuz/ppa-sources-list.html](https://edge.launchpad.net/+help/soyuz/ppa-sources-list.html)

which is what I was reading yesterday before I attempted any of this or posted anything about Firefox and it wasn't really all that helpful.  I spent a lot of [wasted] time in Synaptic Package Manager and finally downloaded that .bz2 archive directly from here:

[http://www.mozilla.com/en-US/firefox/upgrade.html](http://www.mozilla.com/en-US/firefox/upgrade.html)

It extracted fine, but everything I tried with both the firefox and updater files in that subdirectory either left me with the old 3.0.18 version of firefox (or else didn't do anything), so I tried running it as a script, since the documentation was piss-poor on the Mozilla page above.

Then someone posted a helpful page this morning over in the Networking forum here:

[http://ubuntuforums.org/showthread.php?t=1412622](http://ubuntuforums.org/showthread.php?t=1412622)

which links here:

[http://www.ubuntugeek.com/how-to-install-firefox-3-6-stable-from-ubuntu-ppa.html](http://www.ubuntugeek.com/how-to-install-firefox-3-6-stable-from-ubuntu-ppa.html)

After adding those 2 "ppa" repostitories to /etc/apt/sources.list that** sudo apt-get update** command mostly worked, with these warnings:
> Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21
W: You may want to run apt-get update to correct these problems
Of course, that is the same command that I just ran "to correct these problems" if this isn't circular enough yet...

Now I did just see some packages downloaded that looked like they were left over from some Wine updates that I attempted to do last week (that hung my ubuntu 9.04 system and apparently have been hanging "in limbo" for several days).

Finally! this command** sudo apt-get install firefox-3.6** ran successfully with this output:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  firefox-3.6
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 1396B of archives.
After this operation, 36.9kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  firefox-3.6
Install these packages without verification [y/N]? y
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main firefox-3.6 3.6+jaunty [1396B]
Fetched 1396B in 0s (3462B/s)     
Selecting previously deselected package firefox-3.6.
(Reading database ... 515347 files and directories currently installed.)
Unpacking firefox-3.6 (from .../firefox-3.6_3.6+jaunty_all.deb) ...
Setting up firefox-3.6 (3.6+jaunty) ...
Of course, I already had a working copy of Firefox 3.6 installed last night with my "rigged" Firefox panel launcher/icon (but now my Applications > Internet > Firefox link actually takes me to Firefox 3.6 instead of Firefox 3.0.18 like it did all last night).  Also, my add-ins/plugins are working just like they did last night- so no changes there.

Overall, one of the worst things I've ever had to deal with under Linux (and I used to compile/optimize and customize kernels back in the RedHat days).

Nice work, Mozilla! ](*,)

edit:  I'm not seeing anything about 64-bit versions though (I read that Mozilla doesn't do those in several places yesterday).

---

### Post by bodhi.zazen on 2010-02-21
I updated the title for you ;)

---

