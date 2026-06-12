---
title: "Update Manager"
date: 2010-08-22
forum: General Help
---

### Post by corrytonapple on 2010-08-22
How do I get the Update manager to stop bugging me to install the flash plugins?
Thanks

---

### Post by ajgreeny on 2010-08-22
To install or update flash plugins?  Normally it only has packages that are already installed listed, unless a new dependency has arisen from an updated package.

Can I assume you do not have flash plugin installed at the moment?

---

### Post by zvacet on 2010-08-22
For any package you don´t want to upgrade go to the synaptic>find that package>package tab>lock version.

---

### Post by corrytonapple on 2010-08-22
> **ajgreeny said:**
> To install or update flash plugins?  Normally it only has packages that are already installed listed, unless a new dependency has arisen from an updated package.

Can I assume you do not have flash plugin installed at the moment?
Yes. How can I get that Update Manager Window back?

---

### Post by ajgreeny on 2010-08-22
> **zvacet said:**
> For any package you don´t want to upgrade go to the synaptic>find that package>package tab>lock version.
I think, though I'm not certain, that this method will only stop synaptic showing the package, and it will still appear in update manager.

You probably need to pin the version you have.
To pin a package version add these lines to  /etc/apt/preferences:
```
Package: name
Pin: version (number from repos)    
Pin-Priority: 1001
```

---

### Post by corrytonapple on 2010-08-22
Is that a terminal? How do I get to ect.?

---

### Post by lovinglinux on 2010-08-22
You should update flash, since all previous versions have a critical vulnerability.

Is there a particular reason why you don't want to update it?

---

### Post by corrytonapple on 2010-08-22
I started a new user account and even though firefox is the same as in my main account, it won't show flash pages. Your firefox extension is also installed.

---

### Post by lovinglinux on 2010-08-22
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

### Post by corrytonapple on 2010-08-22
Info for Number one In Screenshot One
Info for Number two in Screenshot Two
Info for Number Three:
```

Ubuntu Architecture

Linux Todds-laptop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox                        install
firefox-branding                install
firefox-gnome-support                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.8/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

dropbox.list
google-chrome.list
google-chrome.list.save
lucid-partner.list
lucid-partner.list.save
ubuntu-tweak-stable.list
ubuntu-tweak-stable.list.save

Flash packages

flashplugin-installer                install
flashplugin-nonfree                install

Plugin locations

/usr/lib/firefox-addons/plugins/libflashplayer.so
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

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/flashplugin-alternative.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped

```
Thats it.

---

### Post by lovinglinux on 2010-08-22
What happens when you open flash video page?

---

### Post by corrytonapple on 2010-08-22
Well, Firefox Crashes. I just avoid those pages and go to our iMac for that. I am posting now from Chrome.

---

### Post by lovinglinux on 2010-08-22
Have you tried to create a third user to see if the problem persists?

Do you have moonlight installed? If yes, then remove libmoon.

---

### Post by corrytonapple on 2010-08-22
I don't know what moonlight is. I do have a third user. Actually, I have a primary personal account that works fine thanks to you, I have my brother's account where I first saw the problem, and then corrytonapple for taking screenshots where I realized flash does not work either. According to Foxytunes, my extensions folder is corrupted. Is that the problem?
Will report back tommorrow afternoon.

---

### Post by lovinglinux on 2010-08-22
> **corrytonapple said:**
> I don't know what moonlight is. I do have a third user. Actually, I have a primary personal account that works fine thanks to you, I have my brother's account where I first saw the problem, and then corrytonapple for taking screenshots where I realized flash does not work either. According to Foxytunes, my extensions folder is corrupted. Is that the problem?

Could be. Create a new profile for the user with the corruption. to do that, close Firefox and start the profile manager with:

```
firefox -P
```

---

### Post by corrytonapple on 2010-08-24
All it does is open a new firefox window and bring me to my homepage.

---

### Post by lovinglinux on 2010-08-24
> **corrytonapple said:**
> All it does is open a new firefox window and bring me to my homepage.

You need to close Firefox before running that command or use the no remote option:

```
firefox -no-remote -P
```

---

### Post by corrytonapple on 2010-08-24
OK, Done. Now reinstall extensions?

---

### Post by lovinglinux on 2010-08-24
> **corrytonapple said:**
> OK, Done. Now reinstall extensions?

Does it work without problems now? If yes, then install extensions one by one and test.

See [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

---

### Post by corrytonapple on 2010-08-31
Yes, it works now. Thanks Lovinglinux. Well, now you've helped me twice. I am reinstalling addons now. Sorry for the late reply. Lots of school things needing to be done. I also updated flash and your addon and they work great again.
Thanks again! I love this community.....................

---

### Post by lovinglinux on 2010-09-01
> **corrytonapple said:**
> Yes, it works now. Thanks Lovinglinux. Well, now you've helped me twice. I am reinstalling addons now. Sorry for the late reply. Lots of school things needing to be done. I also updated flash and your addon and they work great again.
Thanks again! I love this community.....................

You are welcome.

---

