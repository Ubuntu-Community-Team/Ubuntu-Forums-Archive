---
title: "Every time I install updates, problems with Internet"
date: 2010-11-13
forum: General Help
---

### Post by rva1945 on 2010-11-13
This is the second time (now I don't want to install any more updates) I have problems with Firefox. Now that everything seemed to work fine, after the last update, when I tried to see a youtube video, a message appeared saying that I had to update the Adobe plugin and two more plugins; tried that, but it said that Adobe was "already installed", then I upgraded the second option, Gnome..etc .(I don't remember what else it said), now the message disappeared but I can't see the vids, not even my videos, recently uploaded or older ones, the play button is missing.

???

---

### Post by cgroza on 2010-11-13
You did the updates separately?

---

### Post by Zhukov on 2010-11-13
Check with Synaptic if only one flash plugin is installed...

Also, try it with Chrome.

This way we can pinpoint some issues...

---

### Post by Dex73 on 2010-11-13
This sounds like a random upgrade required for video. Though it could be a problem with not getting the upgrades from upgrade manager. Are all your settings good there? Especially anything to do with flash.

---

### Post by rva1945 on 2010-11-14
> **cgroza said:**
> You did the updates separately?

I just did as always, just accepted the updates. Of course I restartred Ubuntu afterwards.

---

### Post by rva1945 on 2010-11-14
> **Zhukov said:**
> Check with Synaptic if only one flash plugin is installed...

Also, try it with Chrome.

This way we can pinpoint some issues...

I don't have the Chrome but the same problem happens in Seamonkey.

Went to Synaptic package manager, searched for flash, and I see these ones as installed:

(Package/Installed version)

flashplugin-installer / 10.1.102.64ubuntu0.9.10.1
flashplugin-nonfree / 10.1.102.64ubuntu0.9.10.1
flasm / 1.62-3
gnash / 0.8.6-0ubuntu1
libswfdec-0.8-0 / 0.8.4-1
swfdec-mozilla / 0.8.2-1ubuntu2

I'd appareciate any help.
Robert

---

### Post by rva1945 on 2010-11-14
> **rva1945 said:**
> I don't have the Chrome but the same problem happens in Seamonkey.

Went to Synaptic package manager, searched for flash, and I see these ones as installed:

(Package/Installed version)

flashplugin-installer / 10.1.102.64ubuntu0.9.10.1
flashplugin-nonfree / 10.1.102.64ubuntu0.9.10.1
flasm / 1.62-3
gnash / 0.8.6-0ubuntu1
libswfdec-0.8-0 / 0.8.4-1
swfdec-mozilla / 0.8.2-1ubuntu2

I'd appareciate any help.
Robert

I attached 4 screenshots of the Synaptic package manager, searched for flash

---

### Post by gandaran on 2010-11-14
for flash to work properly you can only have one package installed!
flashplugin-installer / 10.1.102.64ubuntu0.9.10.1 is the recommended one.

---

### Post by rva1945 on 2010-11-14
> **gandaran said:**
> for flash to work properly you can only have one package installed!
flashplugin-installer / 10.1.102.64ubuntu0.9.10.1 is the recommended one.


Then what should I do? uninstall all except 10.1.102.64ubuntu0.9.10.1?

---

### Post by gandaran on 2010-11-14
> **rva1945 said:**
> Then what should I do? uninstall all except 10.1.102.64ubuntu0.9.10.1?
yes, remove gnash and swfdec plugins, and reinstall the adobe flashplugin-installer package, you cant have three conflicting flash plugins installed!

---

### Post by rva1945 on 2010-11-14
> **gandaran said:**
> for flash to work properly you can only have one package installed!
flashplugin-installer / 10.1.102.64ubuntu0.9.10.1 is the recommended one.

Well, I uninstallñed the others, now when I try to see a youtube video:

You need to upgrade your Adobe Flash Player to watch this video. 
 [Download it from Adobe.]("http://get.adobe.com/flashplayer/")

I click on the Adobe link, then I have to select the version to download (I vahe Ubuntu 9.10):

TUM for Linux
tar.gz for Linux
.rpm for Linux
.deb for Ubuntu 8.04+
.APT for Ubuntu 9.04+

now?

---

### Post by gandaran on 2010-11-14
> **rva1945 said:**
> Well, I uninstallñed the others, now when I try to see a youtube video:

You need to upgrade your Adobe Flash Player to watch this video. 
 [Download it from Adobe.]("http://get.adobe.com/flashplayer/")

I click on the Adobe link, then I have to select the version to download (I vahe Ubuntu 9.10):

TUM for Linux
tar.gz for Linux
.rpm for Linux
.deb for Ubuntu 8.04+
.APT for Ubuntu 9.04+

now?
did you reinstalled the package and removed the flashplugin-nonfree as well? and don't install anything else, all you need is the flashplugin-installer package
post the output of this command
```
locate libflash
```

---

### Post by rva1945 on 2010-11-14
> **gandaran said:**
> did you reinstalled the package and removed the flashplugin-nonfree as well? and don't install anything else, all you need is the flashplugin-installer package
post the output of this command
```
locate libflash
```

The output of the command:

robert@rvasystem:~$ locate libflash
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/openoffice/basis3.1/program/libflashli.so
/usr/share/ubufox/plugins/libflashplayer.so
robert@rvasystem:~$

---

### Post by gandaran on 2010-11-14
> **rva1945 said:**
> The output of the command:

robert@rvasystem:~$ locate libflash
[COLOR="DarkRed"]/usr/lib/firefox-addons/plugins/libflashplayer.so[/COLOR]
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/openoffice/basis3.1/program/libflashli.so
[COLOR="DarkRed"]/usr/share/ubufox/plugins/libflashplayer.so[/COLOR]
robert@rvasystem:~$
I think you have installed a lot of flash plugins and now your system is messed up!
you shouln't have the ones in red, look maybe it's best to install the flash-aid firefox addon, this addon removes all conflicting plugins and installs the correct one.
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by rva1945 on 2010-11-14
> **rva1945 said:**
> The output of the command:

robert@rvasystem:~$ locate libflash
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/openoffice/basis3.1/program/libflashli.so
/usr/share/ubufox/plugins/libflashplayer.so
robert@rvasystem:~$

The only flash pligin that now remained installed was the installer; I marked it for complete removal, applied the changes,

Then I wet to see a youtube video, a message says that I need to upgrade the Adobe Flash Player, I click on missing plugins, these appear:

Adobe Flash Player installer
Swfdec SWF Player
Gnash SWF Player

Y select the first one, next next until I get the message saying that it is installed.

Then I try to see a video, the same results, 

You need to upgrade your Adobe Flash Player to watch this video. 
 [Download it from Adobe.]("http://get.adobe.com/flashplayer/")

In Synoptic, the only flash plugin installed is the flashplugin-installed, version 10.1.102.64ubuntu0.9.10.1, but I stil can't see the vids.

---

### Post by gandaran on 2010-11-14
> **rva1945 said:**
> The only flash pligin that now remained installed was the installer; I marked it for complete removal, applied the changes,

Then I wet to see a youtube video, a message says that I need to upgrade the Adobe Flash Player, I click on missing plugins, these appear:

Adobe Flash Player installer
Swfdec SWF Player
Gnash SWF Player

Y select the first one, next next until I get the message saying that it is installed.

Then I try to see a video, the same results, 

You need to upgrade your Adobe Flash Player to watch this video. 
 [Download it from Adobe.]("http://get.adobe.com/flashplayer/")

In Synoptic, the only flash plugin installed is the flashplugin-installed, version 10.1.102.64ubuntu0.9.10.1, but I stil can't see the vids.

if it says you need to upgrade flash it's because you have an old flashplugin installed!

---

### Post by rva1945 on 2010-11-14
> **gandaran said:**
> if it says you need to upgrade flash it's because you have an old flashplugin installed!

But I uninstall the plugin and then I follow the Adobe directives ! Someone at the forum told me that 10.1.102.64 is the correct one.

---

### Post by gandaran on 2010-11-14
> **rva1945 said:**
> But I uninstall the plugin and then I follow the Adobe directives ! Someone at the forum told me that 10.1.102.64 is the correct one.
no you haven't removed it, this plugin was installed manually not in package manager!
see those lines I marked in red, go to those folders and delete the libflashplayer.so file then reinstall the flashplugin-installer package (close firefox) or install the flash-aid addon to do it.

---

### Post by rva1945 on 2010-11-14
> **gandaran said:**
> if it says you need to upgrade flash it's because you have an old flashplugin installed!

I thought I didn't have Chrome installed but yes, it's installed, and yes I can see the youtube videos in Chrome browser.

Now hat do I fix the problem in Firefox?

---

### Post by gandaran on 2010-11-14
> **rva1945 said:**
> I thought I didn't have Chrome installed but yes, it's installed, and yes I can see the youtube videos in Chrome browser.

Now hat do I fix the problem in Firefox?
chrome works with it's own built in flash.

---

### Post by gandaran on 2010-11-14
to check which flash plugin is installed type in firefox url bar
```
about:plugins
```
look for (all) the shockwave flash versions and post them here.

---

### Post by rva1945 on 2010-11-14
> **gandaran said:**
> i think you have installed a lot of flash plugins and now your system is messed up!
You shouln't have the ones in red, look maybe it's best to install the flash-aid firefox addon, this addon removes all conflicting plugins and installs the correct one.
[https://addons.mozilla.org/en-us/firefox/addon/161939/](https://addons.mozilla.org/en-us/firefox/addon/161939/)


thanks man, it worked!

---

