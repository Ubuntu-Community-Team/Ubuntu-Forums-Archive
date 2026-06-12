---
title: "Flash with working sound but no video in Firefox."
date: 2010-12-18
forum: General Help
---

### Post by compiz addict on 2010-12-18
I'm using Ubuntu 10.10 Desktop, and I can't see flash in Firefox. I can hear flash, but not see it. I'm not sure when this started, because I haven't been using Firefox in a while. I've been using Chrome but now I want to use Firefox 4 beta (which also has the same flash problem as Firefox).

---

### Post by bobcollard on 2010-12-18
> **compiz addict said:**
> I'm using Ubuntu 10.10 Desktop, and I can't see flash in Firefox. I can hear flash, but not see it. I'm not sure when this started, because I haven't been using Firefox in a while. I've been using Chrome but now I want to use Firefox 4 beta (which also has the same flash problem as Firefox).
Are you using x86 or amd64 version of Ubuntu 10.10?  Check your Synaptic Package Manager, search for flash.  Should have flashplugin-nonfree and flashplugin-installer both installed.

---

### Post by compiz addict on 2010-12-18
I'm using 32 bit. flashplugin-nonfree wasn't installed, so I installed it and restarted my PC. Didn't fix it though.

---

### Post by bobcollard on 2010-12-18
> **compiz addict said:**
> I'm using 32 bit. flashplugin-nonfree wasn't installed, so I installed it and restarted my PC. Didn't fix it though.
Check for ubuntu-restricted-extras.

---

### Post by lovinglinux on 2010-12-19
Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

---

### Post by compiz addict on 2010-12-19
Weird, I thought I had the restricted extras but I guess not. That didn't fix it though, nor did Flash-AID (although now I have a cool flash button in my Firefox toolbar XD)

---

### Post by bobcollard on 2010-12-19
> **compiz addict said:**
> Weird, I thought I had the restricted extras but I guess not. That didn't fix it though, nor did Flash-AID (although now I have a cool flash button in my Firefox toolbar XD)
nspluginwrapper is the last thing I can think of you might need.  Sorry, I'm just a user and these things don't come to me all at once.

---

### Post by compiz addict on 2010-12-19
Will I have to restart my computer for that to take effect?

---

### Post by bobcollard on 2010-12-19
> **compiz addict said:**
> Will I have to restart my computer for that to take effect?
Log out, it's quicker.

---

### Post by compiz addict on 2010-12-19
Oh yeah. Somehow I still remember the ol' Windows days when I had to restart 24/7.

Unfortunately it still didn't fix it.

I remember that before I upgraded to Maverick I tried RGBA (to make the backgrounds of windows transparent) and it messed some things up like my desktop, but I got rid of it. Do you think that could cause an issue?

---

### Post by bobcollard on 2010-12-19
Not sure what that is.  Open terminal and enter the following command:
```
sudo apt-get autoremove
```
This will get rid of any dependents that may have been left over from things you removed.

---

### Post by lovinglinux on 2010-12-19
Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

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

### Post by techunit on 2010-12-19
You could try purging the flash packages before you reinstall them. Sometimes this helps.

---

### Post by compiz addict on 2010-12-19
*bump*

EDIT: Oops, didn't see 2nd page

---

### Post by compiz addict on 2010-12-19
File:  /usr/lib/flashplugin-installer/libflashplayer.soVersion:   Shockwave Flash 10.1 r102I'm using Firefox 4.0 beta. I also have the non-beta Firefox. Too lazy to check the version because I already did 5 times, each time forgetting I was sending this reply and closing the forum.

```

Ubuntu Architecture

Linux eric-desktop 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox                        install
firefox-3.0                    deinstall
firefox-4.0                    install
firefox-4.0-core                install
firefox-branding                install
firefox-gnome-support                install
kubuntu-firefox-installer            install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.14pre/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

canonical-dx-team-une-lucid.list
canonical-dx-team-une-lucid.list.distUpgrade
canonical-dx-team-une-lucid.list.save
crebs-ppa-maverick.list
crebs-ppa-maverick.list.save
erik-b-andersen-rgba-gtk-lucid.list
erik-b-andersen-rgba-gtk-lucid.list.distUpgrade
erik-b-andersen-rgba-gtk-lucid.list.save
erik-b-andersen-rgba-gtk-maverick.list
gdm2setup-gdm2setup-maverick.list
gdm2setup-gdm2setup-maverick.list.save
glennric-dolphin-emu-maverick.list
glennric-dolphin-emu-maverick.list.save
google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
google-talkplugin.list
hel-sheep-pastie-maverick.list
hel-sheep-pastie-maverick.list.save
mixxxdevelopers-ppa-maverick.list
mixxxdevelopers-ppa-maverick.list.save
ubuntu-mozilla-daily-ppa-maverick.list
ubuntu-mozilla-daily-ppa-maverick.list.save
ubuntu-tweak-stable.list
ubuntu-tweak-stable.list.distUpgrade
ubuntu-tweak-stable.list.save

Flash packages

flashplugin-installer                install
flashplugin-nonfree                install

Plugin locations

/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so

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
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

```

---

### Post by lovinglinux on 2010-12-20
> **compiz addict said:**
> File:  /usr/lib/flashplugin-installer/libflashplayer.soVersion:   Shockwave Flash 10.1 r102I'm using Firefox 4.0 beta. I also have the non-beta Firefox. Too lazy to check the version because I already did 5 times, each time forgetting I was sending this reply and closing the forum.

[code]
Ubuntu Architecture

Linux eric-desktop 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux

...

Everything looks normal in your report.

Try using flash 10.2 beta http://labs.adobe.com/downloads/flashplayer10.html

Also see [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html). Apply the tweak for full screen issues.

Also delete ./macromedia folder (you will lose flash games scores).

---

### Post by compiz addict on 2010-12-20
Where do I put the library? Does it go in /usr/lib?

---

### Post by compiz addict on 2010-12-20
Ok, found where it goes.

Also removed RGBA (guess I never removed it 100%) with the instructions at [http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html](http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html)

Re-logged in, and it worked!

It was probably removing RGBA that fixed it, but now I even get to beta test the new flash XD. I'm obviously the beta-testing kind of person (else I wouldn't have had this problem in the first place).

Thanks for all help.

---

### Post by lovinglinux on 2010-12-23
> **compiz addict said:**
> Ok, found where it goes.

Also removed RGBA (guess I never removed it 100%) with the instructions at [http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html](http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html)

Re-logged in, and it worked!

It was probably removing RGBA that fixed it, but now I even get to beta test the new flash XD. I'm obviously the beta-testing kind of person (else I wouldn't have had this problem in the first place).

Thanks for all help.

Glad to read that you have fixed it. BTW, you are not the first one to complain about RGBA screwing flash.

---

