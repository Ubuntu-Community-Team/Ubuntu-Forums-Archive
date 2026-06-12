---
title: "Updating Firefox"
date: 2009-10-26
forum: General Help
---

### Post by bds28338 on 2009-10-26
so, my Firefox is stuck at 3.0 something and I wanted to update to 3.5 which I see on the Mozilla website. In the Help section of Firefox the Check for Updates is greyed out, why is that? Also, if I just download a new program from the respective website and install it with the installer, is it going to register in Synaptic and Add/Remove? Will the Ubuntu Updater still look for updates for it?

---

### Post by holycow131415 on 2009-10-26
3.5.3 is code named Sheriko. if you install it from add/remove, the other firefox will stll be installed, so you will have to remove it. its greyed out because that is only for windows. updating will need you add packages from a PPA for daily builds from a firefox site.

---

### Post by Bradj47 on 2009-10-26
I thought the Update Manager was updating mine, but when I check Help -> About Mozilla Firefox, it turns out I'm running 3.0.14. And 'Check for Updates' is greyed out for me too. Weird...

---

### Post by holycow131415 on 2009-10-26
Yes its supposed to be greyed out in linux. You need to add a PPA to update your firefox 3.5.3 once it is installed.

---

### Post by bds28338 on 2009-10-26
Ppa?

---

### Post by holycow131415 on 2009-10-26
[http://www.blogsdna.com/3824/how-to-download-install-firefox-35-on-ubuntu-904-linux.htm](http://www.blogsdna.com/3824/how-to-download-install-firefox-35-on-ubuntu-904-linux.htm)

---

### Post by bds28338 on 2009-10-26
I was reading up on this right here, [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

and if I'm reading it right, eventually I can get the 3.5 version of Firefox through the Update Manager, I just have to wait a little while?

---

### Post by Uncle Spellbinder on 2009-10-27
> **holycow131415 said:**
> 3.5.3 is code named Sheriko. if you install it from add/remove, the other firefox will stll be installed, so you will have to remove it. its greyed out because that is only for windows. updating will need you add packages from a PPA for daily builds from a firefox site.

No. 3.5.3 is not Shiretoko. 3.5.3 is the current, public release build. 3.5.4 is to be released in less than a week. 3.5.5 (codenamed "Shiretoko") is the daily build available through PPA...

Add this to the Jaunty sources.list for Firefox 3.5.5

```
## FIREFOX 3.5 (SHIRETOKO)
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
##sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE
```

More in the PPA's [**here**](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa) (Firefox 3.6 and 3.7 builds)

---

### Post by lovinglinux on 2009-10-27
The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences.

---

