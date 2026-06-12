---
title: "how to install java"
date: 2010-02-07
forum: General Help
---

### Post by venku on 2010-02-07
hey anyone plz help me how can i install java in ubuntu 9.10

---

### Post by MelDJ on 2010-02-07
see: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by scouser73 on 2010-02-07
> **venku said:**
> hey anyone plz help me how can i install java in ubuntu 9.10

Hi Venku, to install the latest version of Java please follow the instructions on this website: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by Uncle Spellbinder on 2010-02-07
I installed everything Java related with...

```
sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java6-fonts gsfonts-x11 java-common odbcinst1debian1 sun-java6-bin unixodbc
```

---

### Post by scouser73 on 2010-02-07
> **alixrao said:**
> Hello I am having some problems in installing java.When i install they are having some registry errors in the system.Please tell what should i do?

You're using Ubuntu yes?

---

### Post by scouser73 on 2010-02-07
> **Uncle Spellbinder said:**
> I installed everything Java related with...

```
sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java6-fonts gsfonts-x11 java-common odbcinst1debian1 sun-java6-bin unixodbc
```

That only installs Java ver. 15 doesn't it? I'm sure I've heard that Ubuntu won't be updating Java anymore, so people will have to manually install it.

---

### Post by Uncle Spellbinder on 2010-02-07
> **scouser73 said:**
> That only installs Java ver. 15 doesn't it? I'm sure I've heard that Ubuntu won't be updating Java anymore, so people will have to manually install it.

Yes, you're right. Going to remove what I have and try the tutorial here: [http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU-9.10](http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU-9.10)

Tanks for the heads-up. ;)

---

### Post by Uncle Spellbinder on 2010-02-07
Using this guide: [http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU-9.10](http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU-9.10)

Worked flawlessly!

**Generated:** Sun Feb 07 2010 13:10:58 GMT-0500 (EST)
**User Agent:** Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2) Gecko/20100115 Firefox/3.6
**Build ID:** 20100115133306

**Enabled Extensions:** [15]
- [Adblock Plus](http://adblockplus.org/) 1.1.3
- [Add to Search Bar](http://firefox.maltekraus.de/extensions/add-to-search-bar) 2.0
- [Add-on Collector](http://www.google.com/search?q=Firefox%20Add-on%20Collector) 1.0.4
- [BBCode](http://www.mrtech.com/extensions/#bbcode) 0.5.3.1
- [Compact Menu 2](https://addons.mozilla.org/firefox/user/108029) 3.1.0
- [CuteMenus - Crystal SVG](http://www.cutemenuproject.com/) 1.9.3
- [DownloadHelper](http://www.downloadhelper.net) 4.7
- [Flagfox](http://flagfox.net/) 3.3.20
- [FlashGot](http://flashgot.net) 1.2.1.10
- [MR Tech Toolkit](http://www.mrtech.com/extensions/) 6.0.4
- [OptimizeGoogle](http://www.optimizegoogle.com/) 0.77
- [Paste Email (original)](http://customsoftwareconsult.com/extensions) 3.2.2
- [Secure Login](https://blueimp.net/mozilla/) 0.9.3
- [Stylish](http://userstyles.org/) 1.0.7
- [Tab Clicking Options](http://twanno.mozdev.org/) 0.6.9

**Installed Themes:** [2]
- [Default](http://www.mozilla.org/)
- **[Nemesis](http://www.google.com/search?q=Firefox%20Nemesis) 2010.02.02**

**Installed Plugins:** (14)
- Adobe Reader 9.3
- Default Plugin
- DivX Browser Plug-In
- DivX® Web Player
- iTunes Application Detector
**[COLOR="Red"]- Java(TM) Plug-in 1.6.0_18[/COLOR]**
- mplayerplug-in is now gecko-mediaplayer 0.9.8
- QuickTime Plug-in 7.2.0
- QuickTime Plug-in 7.4.5
- RealPlayer 9
- Shockwave Flash
- VLC Multimedia Plugin (compatible Totem 2.28.2)
- Windows Media Player Plug-in
- Windows Media Player Plug-in 10 (compatible; Totem)

---

