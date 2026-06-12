---
title: "Firefox flash plugin not working"
date: 2011-06-03
forum: General Help
---

### Post by rowbird on 2011-06-03
Hi all, I have installed Flash Plugin NonFree, but it doesn't show up in Firefox v3.x.x about:plugins. Does anybody know why. Flash works in Chrome however. Thanks in advance.

---

### Post by jim_deadlock on 2011-06-03
Have you tried installing flashplugin-installer from the software centre?

---

### Post by rowbird on 2011-06-03
Yes I selected it from synaptic with no avail.

---

### Post by irv on 2011-06-03
What version of Ubuntu are you using. I see you are not using FF 4. Is there any reason that you are using an older version?

---

### Post by rowbird on 2011-06-03
Maverick Meercat is my system. I will try to remove Firefox 3 and install Firefox 4.

---

### Post by irv on 2011-06-03
> **rowbird said:**
> Maverick Meercat is my system. I will try to remove Firefox 3 and install Firefox 4.

When I was using 10.04 and 10.10 FF 4 worked great. It also ran faster and had some nice plug-ins.

---

### Post by linuxinstalledfromhdd on 2011-06-03
> **rowbird said:**
> Hi all, I have installed Flash Plugin NonFree, but it doesn't show up in Firefox v3.x.x about:plugins. Does anybody know why. Flash works in Chrome however. Thanks in advance.

Try using Flash Aid Plugin for Firefox.

[http://cinderbox.net/2011/03/22/flash-aid-addon-for-firefox-automatically-detects-best-flash-version-for-your-system/](http://cinderbox.net/2011/03/22/flash-aid-addon-for-firefox-automatically-detects-best-flash-version-for-your-system/)

---

### Post by rowbird on 2011-06-04
I tried Flash Aid extension, and still no flash. The browser is telling me to install missing plugins.

---

### Post by lovinglinux on 2011-06-04
> **rowbird said:**
> I tried Flash Aid extension, and still no flash. The browser is telling me to install missing plugins.

Just installing the extension is not enough. You need to run the installation Wizard. Have you done that? If so, then did you get any errors in the terminal output while the extension ran the script? Have you restarted Firefox after running the Wizard? 

Please click the extension "Help" menu, then click "Generate report" then post the contents of the *firefox-report.txt* file that should be created on your Desktop.

---

### Post by rowbird on 2011-06-04
I have ran the plugin using the wizard with no errors, and here is the report which has errors in it. It sounds like some files are missing. Is there a way I can fix it?


Ubuntu Architecture

Linux 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox						install
firefox-globalmenu				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-4.0.1/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

gamers.sources.list
gamers.sources.list.save
mozillateam-firefox-stable-maverick.list
prodoomman-qmlsaver-maverick.list
prodoomman-qmlsaver-maverick.list.save
ultamatix.sources.list
ultamatix.sources.list.save

Flash packages

flashplugin-installer				install
flashplugin-nonfree				install
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

Generated File. Do not edit.

[HEADER]
Version:0.15:$
Arch:x86-gcc3:$

[PLUGINS]

[INVALID]

---

### Post by lovinglinux on 2011-06-04
Indeed it looks like the Wizard ran okay. However, it also looks like Firefox is not detecting any plugins.

Close Firefox, then open the profile folder, which will be under ~/.mozilla/firefox/<profile.name>/ and delete the file *pluginreg.dat*. Start Firefox again, open the Add-on Manager, click the Plugins option and check if there is any plugin listed there. If not, type *about*[noparse]:[/noparse]*plugins* in the address bar and check if it shows any plugin there.

BTW, the errors in your report are normal.

---

### Post by linuxinstalledfromhdd on 2011-06-04
> **rowbird said:**
> Hi all, I have installed Flash Plugin NonFree, but it doesn't show up in Firefox v3.x.x about:plugins. Does anybody know why. Flash works in Chrome however. Thanks in advance.

What kind of system are you using? When did you install Ubuntu? Did you upgrade it recently? 

Make/Model of system?

Do you have any other systems running on this computer besides Ubuntu? 

What were you doing just prior to this issue occuring? Walk it backwards as much as you can. Thanks.:)

---

### Post by irv on 2011-06-04
Do you have the Ubuntu-Restricted-Others installed? 
[ATTACH]194179[/ATTACH]

---

### Post by rowbird on 2011-06-04
I am using Ultimate Edition Lite v2.8 based on 10.10, which is the latest release in this series. I am running it on an Acer Aspire One  model ZG5 SSD drive model netbook. It sat for 2 months with a bummed out bios chip, so I replaced the motherboard, and updated it, and that's when flash wouldn't work in Firefox. I have also installed the package lubuntu-restricted-extras as suggested with no avail.

---

### Post by lovinglinux on 2011-06-04
> **irv said:**
> Do you have the Ubuntu-Restricted-Others installed? 
[ATTACH]194179[/ATTACH]

Flash is already properly installed. The problem is Firefox isn't detecting it.

> **rowbird said:**
> I am using Ultimate Edition Lite v2.8 based on 10.10, which is the latest release in this series. I am running it on an Acer Aspire One  model ZG5 SSD drive model netbook. It sat for 2 months with a bummed out bios chip, so I replaced the motherboard, and updated it, and that's when flash wouldn't work in Firefox. I have also installed the package lubuntu-restricted-extras as suggested with no avail.

Please don't install anything more. Flash is already properly installed. If you start installing other packages, it will make more difficult to troubleshoot.

Have you tried my last suggestion?

If yes, start Firefox via terminal and report if you get any errors in the terminal output.

If not, then do it and generate a new report via Flash-Aid.

---

### Post by rowbird on 2011-06-04
Here are the reports:

**Terminal output:**
(firefox-bin:1662): Gtk-WARNING **: Theme directory  of theme BlueDeck Icons has no size field

**Flash Aid Report:**
Ubuntu Architecture

Linux 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox						install
firefox-globalmenu				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-4.0.1/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

gamers.sources.list
gamers.sources.list.save
mozillateam-firefox-stable-maverick.list
prodoomman-qmlsaver-maverick.list
prodoomman-qmlsaver-maverick.list.save
ultamatix.sources.list
ultamatix.sources.list.save

Flash packages

flashplugin-installer				install
flashplugin-nonfree				install
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

---

### Post by lovinglinux on 2011-06-04
> **rowbird said:**
> Here are the reports:

Please paste the output of the following command:

```
file /usr/share/ubufox/plugins/libflashplayer.so
```

Type *about:addons*, click the Plugins option on the left, then take a screenshot of your your browser and attach here.

Also attach a screenshot of *[noparse]about:plugins[/noparse]* page.

---

### Post by rowbird on 2011-06-04
**Here is the output of that command:**
file /usr/share/ubufox/plugins/libflashplayer.so 
/usr/share/ubufox/plugins/libflashplayer.so: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'

**about:plugins**
No enabled plugins found

---

### Post by lovinglinux on 2011-06-04
> **rowbird said:**
> **Here is the output of that command:**
file /usr/share/ubufox/plugins/libflashplayer.so 
/usr/share/ubufox/plugins/libflashplayer.so: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'

**about:plugins**
No enabled plugins found

Close Firefox, install a different plugin like gecko-mediaplayer, just to see if Firefox can detect it:

```
sudo apt-get install gecko-mediaplayer
```

Start Firefox, go to *[noparse]about:plugins[/noparse]* again and check if the plugin is detected.

---

### Post by rowbird on 2011-06-04
I installed gecko-media-player and checked about:plugins in Firefox and **No enabled plugins found.**

---

### Post by lovinglinux on 2011-06-05
> **rowbird said:**
> I installed gecko-media-player and checked about:plugins in Firefox and **No enabled plugins found.**

So is not a Flash problem. Firefox simply cannot detect any plugin.

Create a [new Firefox profile]("http://www.webgapps.org/tutorials/firefox/general/profiles-and-backups") and check if it can detect the plugins.

---

### Post by rowbird on 2011-06-05
I have created a new profile with no luck either. No plugins found.

---

### Post by lovinglinux on 2011-06-05
Try this:

```
rm -fr ~/.mozilla/plugins
sudo ln -s /usr/lib/mozilla/plugins ~/.mozilla/plugins
```

Restart Firefox and check if the plugins are recognized.

---

### Post by rowbird on 2011-06-05
Tried it and still no plugins recognized. It keeps prompting me to install language packs because it says that they were found in my extensions folder, and when I click to install them, it skips the install and just opens anyway to the browser page.

---

### Post by lovinglinux on 2011-06-05
> **rowbird said:**
> Tried it and still no plugins recognized. It keeps prompting me to install language packs because it says that they were found in my extensions folder, and when I click to install them, it skips the install and just opens anyway to the browser page.

Check the ownership and permissions of the ~/.mozilla folder.

---

### Post by rowbird on 2011-06-05
I am the owner, read and write, of the ~/.mozilla folder. group none, other none.

---

### Post by lovinglinux on 2011-06-05
I am downloading Ultimate Edition to test it on VM. I will need some time to perform some tests.

BTW, run the following commands to revert the last changes we did:

```
unlink ~/.mozilla/plugins
mkdir ~/.mozilla/plugins
```

---

### Post by rowbird on 2011-06-05
I'm using Ultimate Edition Lite LXDE

---

### Post by lovinglinux on 2011-06-05
> **rowbird said:**
> I'm using Ultimate Edition Lite LXDE

I know. I am downloading it.

---

### Post by lovinglinux on 2011-06-05
I wasn't able to install Ultimate Edition on a VM. It simply doesn't boot.

Anyway, try to install Firefox manually, by downloading it from Mozilla ([see my tutorial]("http://www.webgapps.org/tutorials/firefox/general/installing-other-versions")) then test if it can recognize the plugins. Don't skip the plugins instructions of the tutorial, otherwise Firefox won't be able to recognize them.

---

### Post by linuxinstalledfromhdd on 2011-06-05
Try installing just regular Ubuntu 10.10 to a separate partition:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

Sounds like a bug in UE to me.

---

### Post by philinux on 2011-06-08
> **lovinglinux said:**
> Indeed it looks like the Wizard ran okay. However, it also looks like Firefox is not detecting any plugins.

Close Firefox, then open the profile folder, which will be under ~/.mozilla/firefox/<profile.name>/ and delete the file *pluginreg.dat*. Start Firefox again, open the Add-on Manager, click the Plugins option and check if there is any plugin listed there. If not, type *about*[noparse]:[/noparse]*plugins* in the address bar and check if it shows any plugin there.

BTW, the errors in your report are normal.

Dag nabbit, that's what I forgot. pluginreg.dat. I ran flashaid to no avail.

I just decided to run the 32 bit version instead of the old 64 in plugins folder and it was failing to get picked up. Sorted now!! :P

Maybe your flashaid script needs to include deleting that file?

---

### Post by lovinglinux on 2011-06-08
> **philinux said:**
> Dag nabbit, that's what I forgot. pluginreg.dat. I ran flashaid to no avail.

I just decided to run the 32 bit version instead of the old 64 in plugins folder and it was failing to get picked up. Sorted now!! :P

Maybe your flashaid script needs to include deleting that file?

Indeed, that is something to be considered.

---

### Post by decktrio on 2011-06-08
> **lovinglinux said:**
> Just installing the extension is not enough. You need to run the installation Wizard. Have you done that? If so, then did you get any errors in the terminal output while the extension ran the script? Have you restarted Firefox after running the Wizard? 

Please click the extension "Help" menu, then click "Generate report" then post the contents of the *firefox-report.txt* file that should be created on your Desktop.

I have the same problem. When we run the wizard, should we be installing the beta? ...because the version in the repositories didn't help. I'm checking my flash plug-in with YouTube, and I still can't see videos.

EDIT: I just installed the beta version, and that worked perfectly. (Just in case anyone else runs into the same dilemma.)

---

