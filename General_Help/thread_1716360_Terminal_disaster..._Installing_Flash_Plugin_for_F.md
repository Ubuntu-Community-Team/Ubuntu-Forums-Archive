---
title: "Terminal disaster... Installing Flash Plugin for Firefox"
date: 2011-03-28
forum: General Help
---

### Post by Ryan20 on 2011-03-28
(SOLVED)

I've been trying to install the flash plugin for Firefox for a while now since my girlfriend wants to look at Youtube so I found this article on how to do it at:

[http://www.cyberciti.biz/faq/ubuntu-linux-how-to-install-flash-player-for-firefox/](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-install-flash-player-for-firefox/)

I tried and it couldn't get rid of the Adobe Flash Player currently installed because it's in a bad state?   So I tried uninstalling it (poorly I'm guessing) but that didn't work either.  Hopefully someone who knows what they're doing could maybe give me a hand?  

Full story below:

```
acer@acer-AO532h:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for acer: 
Sorry, try again.
[sudo] password for acer: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  flashplugin-installer
Suggested packages:
  xulrunner-1.9 firefox-3.0 konqueror-nsplugins msttcorefonts
  ttf-xfree86-nonfree xfs
The following packages will be REMOVED:
  adobe-flashplugin
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/22.2kB of archives.
After this operation, 229kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: error processing adobe-flashplugin (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
acer@acer-AO532h:~$ sudo apt-get autoremove adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  adobe-flashplugin linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 90.2MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing adobe-flashplugin (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
No apport report written because MaxReports is reached already
                                                              (Reading database ... 
dpkg: warning: files list file for package `adobe-flashplugin' missing, assuming package has no files currently installed.
(Reading database ... 143789 files and directories currently installed.)
Removing linux-headers-2.6.35-22-generic ...
Removing linux-headers-2.6.35-22 ...
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
acer@acer-AO532h:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  flashplugin-installer
Suggested packages:
  xulrunner-1.9 firefox-3.0 konqueror-nsplugins msttcorefonts
  ttf-xfree86-nonfree xfs
The following packages will be REMOVED:
  adobe-flashplugin
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/22.2kB of archives.
After this operation, 229kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: error processing adobe-flashplugin (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
acer@acer-AO532h:~$ 

```

---

### Post by Kirboosy on 2011-03-28
I always just install the "ubuntu-restricted-extras" package in Synaptic Package Manager (System-->Admin-->Synaptic)  and let it install my flash that way. You might also want to try the [flash-aid]("https://addons.mozilla.org/en-us/firefox/addon/flash-aid/") plugin for FireFox. Its not complaining about a broken package so its worth a shot to try a different installation method...

Also that article you were reading was really old...

---

### Post by Ryan20 on 2011-03-28
Thanks for the quick reply!

Tried your method which was more promising.   It eventually came up with a Microsoft EULA for the fonts, I scrolled down to have a quick read and pressed enter but it wouldn't continue.  So I closed the terminal and opened a new one to do the same thing:

...and the story continues:

```
acer@acer-AO532h:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for acer: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
acer@acer-AO532h:~$ sudo apt-get install ubuntu-restricted-extras
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```God damn...

Same thing happens if I put "**sudo apt-get autoremove ubuntu-restricted-areas.**"

EDIT:

Tried your flash-aid but it didn't help out too much either... Sorry.  Going to try the drag and drop method of the libflashplayer.so file into one of the extension folders.  

Question:  when I  install something half-arsed like that, do bits and pieces of the installation  still remain on the system or does it all get wiped out when it's not completely finished?

---

### Post by 3Miro on 2011-03-28
Wow hold on, don't mess any more with your system!

>  Could not get lock /var/lib/dpkg/lock - open 

means that you are trying to run install/remove two things at once.

Either close all Software Centers/Update Managers/terminals and then try again or reboot.

Try using Synaptic Package Manager (System -> Admin), it will help you avoid errors like that.

---

### Post by TBABill on 2011-03-28
When you get that error you are being told you cannot attempt to install software while another installation program/app is already open, even if it is not being used to install at the same time. Ubuntu Software Center/Synaptic/Terminal with apt-get or aptitude. Only one at a time.
 
Easiest may be to just go into synpatic and find the repo version, mark it for complete removal (purges it) and apply, then go back and install whatever you want instead.

---

### Post by Kirboosy on 2011-03-28
For simplicity I would just use Synaptic across the board. With Synaptic you can tell it to do a list of things (you can with terminal as well but its a bit more advanced...) to install or remove...

---

### Post by DinoT1985 on 2011-03-28
keep this for future reference. makes it easier. installs and uninstalls Flash versions.

[https://addons.mozilla.org/en-us/firefox/addon/flash-aid/](https://addons.mozilla.org/en-us/firefox/addon/flash-aid/)

---

### Post by Ryan20 on 2011-03-28
Wow I'm glad I was forced to put down my keyboard and go to work.  Probably would have been staring at a blank screen by now!   Thanks for all the replies. 

I rebooted because I didn't have anything open but was still picking up the same errors.  Once Ubuntu had finished booting I loaded Synaptic Package Manager.

I got this error:

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.What's all that about?  I'll google it but I'll try not to touch anything until I get some answers this time ha ha!

---

### Post by CharlesA on 2011-03-28
It needs to repair.

Run the command it said to run:

```
sudo dpkg --configure -a
```

---

### Post by wojox on 2011-03-28
Open your terminal and 

```
sudo dpkg --configure -a
```

---

### Post by Ryan20 on 2011-03-28
Grâce à mon dieu...   Okay so now it's reached another point where I'd be lost again and close the terminal followed by even more collateral damage.

```
acer@acer-AO532h:~$ sudo dpkg --configure -a
[sudo] password for acer: 
Setting up libfftw3-3 (3.2.2-1) ...
Setting up java-common (0.38) ...
Setting up libcelt0-0 (0.7.1-1) ...
Processing triggers for desktop-file-utils ...
Setting up libenca0 (1.13-2) ...
Processing triggers for man-db ...
Setting up libwildmidi0 (0.2.2-3) ...
Setting up libopenspc0 (0.3.99a-2) ...
Setting up libcdaudio1 (0.99.12p2-9) ...
Processing triggers for hicolor-icon-theme ...
Setting up libflite1 (1.4-release-2) ...
Setting up tzdata-java (2011d-0ubuntu0.10.10) ...
Setting up libgif4 (4.1.6-9) ...
Setting up libmp4v2-0 (1:1.6dfsg-0.2ubuntu9) ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up liboil0.3 (0.3.16-1ubuntu2) ...
Setting up libmms0 (0.6-1) ...
Setting up libzbar0 (0.10+doc-3build1) ...
Setting up libmodplug1 (1:0.8.8.1-1ubuntu1) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Setting up libmpcdec6 (2:0.1~r459-1) ...
Setting up libdca0 (0.0.5-3) ...
Setting up libass4 (0.9.9-1fakesync1) ...
Setting up librtmp0 (2.3-2) ...
Setting up libsoundtouch1c2 (1.3.1-2) ...
Setting up libgme0 (0.5.5-2) ...
Setting up libofa0 (0.9.3-3.1) ...
Setting up libkate1 (0.3.7-3) ...
Setting up libdc1394-22 (2.1.2-3) ...
Setting up libiptcdata0 (1.0.4-1) ...
Setting up gstreamer0.10-plugins-ugly-multiverse (0.10.16-1) ...
Setting up gstreamer0.10-pitfdll (0.9.1.1+cvs20080215-1ubuntu2) ...
Setting up cabextract (1.3-1) ...
Setting up libmimic0 (1.0.4-2build1) ...
Setting up tsconf (1.0-7build1) ...
Setting up libfaac0 (1.26-0.1ubuntu2) ...
Setting up freepats (20060219-1) ...
Setting up adobe-flashplugin (10.2.153.1-0maverick1) ...
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/iceape/plugins/flashplugin-alternative.so (iceape-flashplugin) in auto mode.
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/iceweasel/plugins/flashplugin-alternative.so (iceweasel-flashplugin) in auto mode.
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) in auto mode.
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/firefox/plugins/flashplugin-alternative.so (firefox-flashplugin) in auto mode.
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/xulrunner/plugins/flashplugin-alternative.so (xulrunner-flashplugin) in auto mode.
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/midbrowser/plugins/flashplugin-alternative.so (midbrowser-flashplugin) in auto mode.
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so (xulrunner-addons-flashplugin) in auto mode.
Processing triggers for libglib2.0-0 ...
Setting up libquicktime1 (2:1.1.5-1) ...
Setting up libts-0.0-0 (1.0-7build1) ...
Setting up libdirectfb-1.2-9 (1.2.10.0-4ubuntu2) ...
Setting up libmjpegtools-1.9 (1:1.9.0-0.5ubuntu3) ...
Setting up gstreamer0.10-plugins-bad-multiverse (0.10.20-1ubuntu1) ...
Setting up gstreamer0.10-plugins-bad (0.10.20-1ubuntu1) ...
Setting up ca-certificates-java (20100412) ...
creating /etc/ssl/certs/java/cacerts...
done.
Setting up openjdk-6-jre-headless (6b20-1.9.7-0ubuntu1) ...
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/java to provide /usr/bin/java (java) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/keytool to provide /usr/bin/keytool (keytool) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/pack200 to provide /usr/bin/pack200 (pack200) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/rmid to provide /usr/bin/rmid (rmid) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/rmiregistry to provide /usr/bin/rmiregistry (rmiregistry) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/unpack200 to provide /usr/bin/unpack200 (unpack200) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/orbd to provide /usr/bin/orbd (orbd) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/servertool to provide /usr/bin/servertool (servertool) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/tnameserv to provide /usr/bin/tnameserv (tnameserv) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/lib/jexec to provide /usr/bin/jexec (jexec) in auto mode.
Setting up openjdk-6-jre-lib (6b20-1.9.7-0ubuntu1) ...
Setting up libaccess-bridge-java (1.26.2-5) ...
Setting up libaccess-bridge-java-jni (1.26.2-5) ...
Setting up openjdk-6-jre (6b20-1.9.7-0ubuntu1) ...
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/javaws to provide /usr/bin/javaws (javaws) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/pluginappletviewer to provide /usr/bin/pluginappletviewer (pluginappletviewer) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/policytool to provide /usr/bin/policytool (policytool) in auto mode.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
acer@acer-AO532h:~$ 
```How do I continue?

---

### Post by CharlesA on 2011-03-28
Looks like it completed fine.

---

### Post by Ryan20 on 2011-03-28
Thanks, sorry I'm taking it so slow now.  Last time I closed the terminal too early, all hell broke loose. 

So I loaded the Package Manager and searched 'flash."  I have a few options here but the flashplugin-nonfree-extrasou..." (runs off my tiny screen) looks like the best option.  Information on it says:

> Adobe Flash Player platform support library for Esound and OSS

This is an open Source extension library for the Adobe Flash Player
that enables support for otherwise unsupported sound systems.  It
provides the libflashsupport.so plugin.  The sound system to use is
automatically detected:

 * It first tries to detect Esound,
 * Next, it checks for OSS.

If all of the above failed, it falls back to the ALSA driver that's
built directly into FlashPlayer 9.

For PulseAudio support, see flashplugin-nonfree-pulse.

Canonical does not provide updates for flashplugin-nonfree-extrasound. Some updates may be provided by the Ubuntu community.All good to go?

EDIT:

Or is this one better?  I searched "adobe" and got flashplugin-installer. 

Information:

> 
Adobe Flash Player plugin installer

Downloads and Installs the Adobe Flash Player plugin. The Adobe Flash Player
plugin supports playing of media and other dynamic content online.

The Adobe Flash Player plugin will work with a range of web-browsers including,
limited to:
 * Firefox
 * Chromium
 * SeaMonkey
 * Iceweasel
 * Iceape
 * Galeon
 * Epiphany
 * Konqueror

WARNING: Installing this Ubuntu package causes the Adobe Flash Player plugin to
be downloaded from [www.adobe.com]("http://www.adobe.com"). The distribution license of the Adobe Flash
Player plugin is available at [www.adobe.com]("http://www.adobe.com"). Installing this Ubuntu package
implies that you have accepted the terms of that license.

Canonical does not provide updates for flashplugin-installer. Some updates may be provided by the Ubuntu community.EDIT:

The only option for the flashplugin-installer is uninstall!

I'm guessing I should do this and then run in the terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

No?  I believe it was the broken Adobe Flash Player that was causing the trouble in the first place.

---

### Post by garvinrick4 on 2011-03-28
rick@rick-HP:~$ aptitude show flashplugin-installer
```
Package: flashplugin-installer           
State: installed
Automatically installed: no
Version: 10.2.153.1ubuntu1
Priority: optional
Section: multiverse/web
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 188 k
Depends: nspluginwrapper (>= 0.9.91.4-2ubuntu1), ia32-libs (>= 2.2ubuntu18),
         debconf | debconf-2.0, wget, fontconfig
Recommends: libasound2-plugins (>= 1.0.16)
Suggests: firefox, xulrunner-1.9, firefox-3.0, konqueror-nsplugins,
          x-ttcidfont-conf, msttcorefonts, ttf-bitstream-vera | ttf-dejavu,
          ttf-xfree86-nonfree, xfs (>= 1:1.0.1-5)
Conflicts: flashplayer-mozilla, flashplugin (< 6), flashplugin-nonfree (<
           10.0.22.87ubuntu2~), libflashsupport, xfs (< 1:1.0.1-5)
Replaces: flashplugin (< 6), flashplugin-nonfree
Provides: flashplugin-nonfree
Description: Adobe Flash Player plugin installer
 Downloads and Installs the Adobe Flash Player plugin. The Adobe Flash Player
 plugin supports playing of media and other dynamic content online. 
 
 The Adobe Flash Player plugin will work with a range of web-browsers including,
 limited to: 
 * Firefox 
 * Chromium 
 * SeaMonkey 
 * Iceweasel 
 * Iceape 
 * Galeon 
 * Epiphany 
 * Konqueror 
   
 WARNING: Installing this Ubuntu package causes the Adobe Flash Player plugin to
 be downloaded from www.adobe.com. The distribution license of the Adobe Flash
 Player plugin is available at www.adobe.com. Installing this Ubuntu package
 implies that you have accepted the terms of that license.
Homepage: http://wiki.ubuntu.com/FlashPlayer9

rick@rick-HP:~$ 

```
If you want to check packages installed or not and what repo's they are in.
sudo apt-get install aptitude
Read up on aptitude is nice tool.

---

### Post by Ryan20 on 2011-03-28
```
apacer@acer-AO532h:~$ aptitude show flashplugin-installer
The program 'aptitude' can be found in the following packages:
 * aptitude
 * aptitude-gtk
Try: sudo apt-get install <selected package>
acer@acer-AO532h:~$ 
```Ahh thanks for the advice.  Don't know why mine pulled up a different result, though it's always good to learn a new command!  

What the heck?   It does the same thing for any packages I type in.

---

### Post by CharlesA on 2011-03-28
It means it isn't installed.

Aptitude is not installed by default on 10.10.

---

### Post by Ryan20 on 2011-03-28
Oh my God.  Sorry I really hope you don't think I'm a lost cause here.  I  appreciate everyone's replies tonight.  I used the package manager to  reinstalled adobe-flashplugin and install flashplugin-nonfree, there  were no conflicts and Youtube ran fine!   
 
 Thanks again to you both and to the guys from earlier, Bill, Mira and Caboose. 

One more question before I head off, is there some sort of good book or documentation I can look at for command lines?  Or do I have to just keep learning this as I go.  Everyone seems to point out how old the articles I drag up are.

---

### Post by CharlesA on 2011-03-28
man pages work wonders.

```
man somecommand
```

---

### Post by Ryan20 on 2011-03-28
Cheers Charles, I'll learn a bit more about that and Aptitude.   Good night to all and thanks again.  Girlfriend will be very happy.

  :popcorn:

---

