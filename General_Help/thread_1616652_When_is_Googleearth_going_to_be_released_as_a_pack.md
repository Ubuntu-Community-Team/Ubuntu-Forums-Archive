---
title: "When is Googleearth going to be released as a package from Medibuntu for Ubuntu 10.10"
date: 2010-11-08
forum: General Help
---

### Post by Nickynak on 2010-11-08
Anybody know, I don't want to downgrade to Lucid just so that I can run Googlearth, but it's been a while now and the package still isn't there for 10.10 on Medibuntu.

---

### Post by gandaran on 2010-11-08
I think it wont ever be released in medibuntu, why not install the .bin package? its easy to install that .bin package or build your own .deb package installing the googleearth-package from synaptic package manager.

---

### Post by coffeecat on 2010-11-08
Just to add to what gandarin said, you need to know the terminal command for running the googleearth-package.

First - open Synaptic and install googleearth-package. That will also install build-essential and a few other things.

Second. Open a terminal and do this command:

```
make-googleearth-package --force
```That will download the GoogleEarthLinux.bin file to your home folder and then build the deb package from it.

Third. Make sure Synaptic has been closed and **either**, from the terminal:

```
sudo dpkg -i googleearth_5.2.1.1588+0.5.7-1_amd64.deb 
```*Change the package name if yours is different.* **OR**:

Simply double-click on the deb package in your home folder and let Software Centre install it.

Fourth. Open it by going to Applications > Internet.

---

### Post by dcstar on 2010-11-09
> **coffeecat said:**
> Just to add to what gandarin said, you need to know the terminal command for running the googleearth-package.
.......

Yep, just what is in the FAQ/HOTWO that people obviously don't bother to read:

[https://help.ubuntu.com/community/GoogleEarth#make-googleearth-package](https://help.ubuntu.com/community/GoogleEarth#make-googleearth-package)

---

### Post by Nickynak on 2010-11-09
DC Star, I already read the posts on here about GoogleEarth and had no success installing it using any of the measures, thats why I posted this thread, as I am waiting for it to come into Medibuntu, as that seemed like the best solution.  Thanks to the other guys posting advice, I will try doing that again, I didn't want to post onto the Googlearth thread as the advice there didn't work for me. Sorry if I upset anybody!

---

### Post by Nickynak on 2010-11-09
With due respect aswell I already went through that FAQ at least twice following it exactly and failed to install Googleearth. I've only been using Linux for this year but am not a total novice, I've used a lot of distros including non-Ubuntu ones, the primary reason I am back on Ubuntu is because the community is usuallly very helpful and friendly here.  Thanks again for all the help.

---

### Post by gandaran on 2010-11-09
> **Nickynak said:**
> With due respect aswell I already went through that FAQ at least twice following it exactly and failed to install Googleearth. I've only been using Linux for this year but am not a total novice, I've used a lot of distros including non-Ubuntu ones, the primary reason I am back on Ubuntu is because the community is usuallly very helpful and friendly here.  Thanks again for all the help.
look I recommend installing the .bin file, its very easy! download the googleearth .bin from google earth website then do exactly this
move the googleearth .bin file to /home/user directory (this is important for less experienced linux users, the file must be in your home user folder!)
then open the terminal and type [COLOR="Navy"]sh[/COLOR] and add exactly the full google earth bin file name then hit enter, thats all, this opens the google earth install window.
this installs google earth in home directory, if you want to install it in root file system then use sudo ([COLOR="Navy"]sudo sh[/COLOR] plus the google earth bin full name)
try it, you will see it's easy.

and please, if you have any difficulties post the errors output from the terminal, we can only help you if we know what you are doing wrong.

---

### Post by ki4jgt on 2010-11-09
Is this normal?
> 
jesse@Remember:~$ make-googleearth-package --force
cat: /etc/mailname: No such file or directory
--2010-11-09 09:33:58--  [http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin)
Resolving dl.google.com... 74.125.45.136, 74.125.45.91, 74.125.45.93, ...
Connecting to dl.google.com|74.125.45.136|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31406473 (30M) [application/octet-stream]
Saving to: `GoogleEarthLinux.bin'

100%[======================================>] 31,406,473  66.0K/s   in 8m 4s   

2010-11-09 09:42:02 (63.4 KB/s) - `GoogleEarthLinux.bin' saved [31406473/31406473]

Google Earth for GNU/Linux 5.2.1.1588
Unrecognized Google Earth version; using anyway (because of --force).
Guessed Google Earth version: 5.2.1.1588
./
./README.linux
./bin/
./bin/googleearth
./googleearth-icon.png
./googleearth.xpm
./linux/
./linux/xdg/
./linux/xdg/xdg-desktop-icon
./linux/xdg/xdg-desktop-menu
./linux/xdg/xdg-mime
./postinstall.sh
./preuninstall.sh
./setup.data/
./setup.data/bin/
./setup.data/bin/Linux/
./setup.data/bin/Linux/x86/
./setup.data/bin/Linux/x86/setup.gtk
./setup.data/bin/Linux/x86/setup.gtk2
./setup.data/bin/Linux/x86/uninstall
./setup.data/bin/Linux/amd64
./setup.data/bin/Linux/x86_64
./setup.data/bin/NetBSD
./setup.data/bin/OpenBSD
./setup.data/bin/FreeBSD
./setup.data/config.sh
./setup.data/locale/
./setup.data/locale/de/
./setup.data/locale/de/LC_MESSAGES/
./setup.data/locale/de/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/de/LC_MESSAGES/setup.mo
./setup.data/locale/es/
./setup.data/locale/es/LC_MESSAGES/
./setup.data/locale/es/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/es/LC_MESSAGES/setup.mo
./setup.data/locale/fr/
./setup.data/locale/fr/LC_MESSAGES/
./setup.data/locale/fr/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/fr/LC_MESSAGES/setup.mo
./setup.data/locale/it/
./setup.data/locale/it/LC_MESSAGES/
./setup.data/locale/it/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/it/LC_MESSAGES/setup.mo
./setup.data/locale/nl/
./setup.data/locale/nl/LC_MESSAGES/
./setup.data/locale/nl/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/nl/LC_MESSAGES/setup.mo
./setup.data/locale/ru/
./setup.data/locale/ru/LC_MESSAGES/
./setup.data/locale/ru/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/ru/LC_MESSAGES/setup.mo
./setup.data/locale/sv/
./setup.data/locale/sv/LC_MESSAGES/
./setup.data/locale/sv/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/sv/LC_MESSAGES/setup.mo
./setup.data/setup.glade
./setup.data/setup.gtk2.glade
./setup.data/setup.xml
./setup.data/splash.xpm
./setup.sh
./googleearth-linux-x86.tar
./googleearth-data.tar
mv: cannot stat `libssl.so.0.9.8': No such file or directory
Checking shlib deps: libge_net.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libfusioncommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
Checking shlib deps: libgeobase.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
Checking shlib deps: libicudata.so.38
Checking shlib deps: libinput_plugin.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
Checking shlib deps: libproj.so.0
Checking shlib deps: libcommon_gui.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
Checking shlib deps: libfusioncommon.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
Checking shlib deps: libgeobaseutils.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libspatial.so'
Checking shlib deps: libcommon.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_platform.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobaseutils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libfusioncommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
Checking shlib deps: gpsbabel
Checking shlib deps: libapiloader.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGMath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGCore.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGUtils.so'
Checking shlib deps: libQtWebKit.so.4
Checking shlib deps: libIGExportCommon.so
Checking shlib deps: libbasicingest.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobaseutils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libfusioncommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
Checking shlib deps: libIGGfx.so
Checking shlib deps: librender.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
Checking shlib deps: libalchemyext.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGMath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGCore.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGAttrs.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGGfx.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGUtils.so'
Checking shlib deps: libcommon_platform.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
Checking shlib deps: libGLU.so.1
Checking shlib deps: libcomponentframework.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
Checking shlib deps: libmeasure.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobaseutils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
Checking shlib deps: libIGOpt.so
Checking shlib deps: libauth.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libreporting.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_gui.so'
Checking shlib deps: libqgif.so
Checking shlib deps: libqjpeg.so
Checking shlib deps: libQtNetwork.so.4
Checking shlib deps: libIGUtils.so


I ask because it's taking forever!!

---

### Post by gandaran on 2010-11-09
> **ki4jgt said:**
> Is this normal?


I ask because it's taking forever!!
yes it does take some time to build the deb package! thats why I recommend installing the bin file, it's a whole lot easier.

---

### Post by ki4jgt on 2010-11-09
Whats with all the warnings?

---

### Post by gandaran on 2010-11-09
> **ki4jgt said:**
> Whats with all the warnings?
ignore them, just wait for the deb package.

---

### Post by ki4jgt on 2010-11-09
GE keeps exiting on me. Once it opens and shows the globe just loading all the info it just shuts off.

---

### Post by lindsay7 on 2010-11-09
Install Tweak for Ubuntu and install G.E. from there.

---

### Post by gandaran on 2010-11-09
> **ki4jgt said:**
> GE keeps exiting on me. Once it opens and shows the globe just loading all the info it just shuts off.
do you have compiz running? I believe compiz an GL conflict, disable compiz and try running GE then.

---

### Post by GiovanniEmex on 2010-11-09
I do too want Google Earth in Medibuntu. I installed Earth via googleearth-package and via the medibuntu Lucyd-repository but the program (although it didn't crash) cannot connect with the server of Ubuntu, like I would have a firewall on the way (whether I have it or not). On the other hand, with the googleearth-package's .deb output the interface was a lot poorer than with the Lucyd one's, although I have all the fonts and libraries that I suppose to have, but when I ran from terminal '$googleearth' I had no error message (with the Lucyd one I had several ones relating about 'im-ibus.so' ).

This system is Ubuntu 10.10 amd64, and I have find a lot of people on the net having the same problem. Maybe all of us are making the same (basic) mistakes and we, noobies, cannot see what's happening.

Right now I was able to uninstall completely the program (after a little search) but I would like to run it in ubuntu, and not being forced to reboot in Windows just for that app, or even installing it in Wine like some folks have done it (I just read someone unable to use the Linux version but he could use the Windows version on Wine without any problem on the same machine).

By the way, Google makes a version of Chrome for Ubuntu amd64 (which I tried) and it works just fine. Why they don't do the same with Earth? I mean, it's not like they don't know this distribution.

---

