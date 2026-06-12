---
title: "Firefox Hotkeys"
date: 2010-07-27
forum: General Help
---

### Post by masque7 on 2010-07-27
Few questions. Why is *Preferences* always under *Edit*? Why is Ctrl+Shift+Y the hotkey to open the download manager? On Windows it's ctrl+J. Ctrl+J/Ctrl+K do the same thing under GNU/Linux.

---

### Post by lovinglinux on 2010-07-27
> **masque7 said:**
> Few questions. Why is *Preferences* always under *Edit*?

Makes sense to me.

> **masque7 said:**
> Why is Ctrl+Shift+Y the hotkey to open the download manager? On Windows it's ctrl+J. Ctrl+J/Ctrl+K do the same thing under GNU/Linux.

I don't know.

On a side note, I saw your in your signature that you recommend Flash 64bit to fix unresponsive button issues. Be aware that 64bit version of flash is no longer supported by Adobe and all available versions have a critical vulnerability.

To fix the button issue on a 32bit version installed on a 64bit machine, do this:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Then add the following line before the last line of that file:

```
export GDK_NATIVE_WINDOWS=1
```

The file content should look like this:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```

Save the file and restart the browser.

---

### Post by masque7 on 2010-07-27
What's the difference between flashplugin-installer and flashplugin-nonfree?

---

### Post by lovinglinux on 2010-07-27
> **masque7 said:**
> What's the difference between flashplugin-installer and flashplugin-nonfree?

flashplugin-nonfree is a transitional package that in fact installs flashplugin-installer, but there is no need for it. You can install flashplugin-installer directly if you want.

---

### Post by masque7 on 2010-07-30
I'm using the FLASH-AID extension, which went through the steps, and got me the latest Flash 10 32-bit installer (for a 64-bit system). Flash works in Chromium, but not in Firefox. Firefox (youtube.com site) keeps prompting me to download Flash 10.

Any ideas?

---

### Post by lovinglinux on 2010-07-30
> **masque7 said:**
> I'm using the FLASH-AID extension, which went through the steps, and got me the latest Flash 10 32-bit installer (for a 64-bit system). Flash works in Chromium, but not in Firefox. Firefox (youtube.com site) keeps prompting me to download Flash 10.

Any ideas?

What version of FLASH-AID you are using?

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
```

---

### Post by masque7 on 2010-07-30
FLASH-AID: 1.0.10

File: /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
Version: Shockwave Flash 10.1 r53


```
firefox -v
Mozilla Firefox 3.6.8, Copyright (c) 1998 - 2010 mozilla.org
```

Firefox report: [http://pastebin.com/y0D2Pftc](http://pastebin.com/y0D2Pftc)

Some behavior explanation:
Switched to 32-bit flash from 64-bit the other day due to your warning. Everything was fine, I had changed npviewer and Flash was working great. Better performance fullscreen, too.

Today, I get that error after some updates. I had Flash installed (flashplugin-installer), but it wasn't working in Firefox, or showing in about:plugins, but in Chromium, it was fine. I re-ran Flash Aid, no luck.  Flash is now working in Firefox again -- not sure for how much longer, or if another update may invoke problems. I am not sure if the aforementioned updates included any for Firefox. I'm not sure how to check my package cache (for dates) to get to the route of this problem.

---

### Post by lovinglinux on 2010-07-30
> **masque7 said:**
> FLASH-AID: 1.0.10

File: /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
Version: Shockwave Flash 10.1 r53


```
firefox -v
Mozilla Firefox 3.6.8, Copyright (c) 1998 - 2010 mozilla.org
```

Firefox report: [http://pastebin.com/y0D2Pftc](http://pastebin.com/y0D2Pftc)

Some behavior explanation:
Switched to 32-bit flash from 64-bit the other day due to your warning. Everything was fine, I had changed npviewer and Flash was working great. Better performance fullscreen, too.

Today, I get that error after some updates. I had Flash installed (flashplugin-installer), but it wasn't working in Firefox, or showing in about:plugins, but in Chromium, it was fine. I re-ran Flash Aid, no luck.  Flash is now working in Firefox again -- not sure for how much longer, or if another update may invoke problems. I am not sure if the aforementioned updates included any for Firefox. I'm not sure how to check my package cache (for dates) to get to the route of this problem.

I don't know what happened. Could be an issue with pluginreg.dat in Firefox profile. Please let me know if the problem comes back.

---

