---
title: "firefox on 11.04 crashing"
date: 2011-07-23
forum: General Help
---

### Post by ottosykora on 2011-07-23
is there any way to install again firefox 3.x on the ubuntu 11.04?

After upgrade from 10.10 to 11.04, the firefox is of no particular use, as the version 5 crashes about every 5 minutes, is not able to work with flash at all apparently. Also many other tasts are with this version  of firefox not possible, search in this forum will crash the firefox too.

I have hp 6550b notebook, did just the upgrade to 11.04 and here the firefox was updated to version 5 unfortunately.

I am running ubuntu in classic mode with no effects.

---

### Post by jramshu on 2011-07-23
Try installing the flashaid plugin for FireFox and it will make sure you are using the most compatible version. May want to consider using chromium-browser. 
```
sudo apt-get install chromium-browser
```

---

### Post by ottosykora on 2011-07-23
what is the flash aid plugin and where do I get it from?

I have even difficulties to read this forum thread, it crashed 3 times until I managed to read the text.

The firefox is kind of needed here, but will try the chromium too.

---

### Post by lovinglinux on 2011-07-23
> **ottosykora said:**
> what is the flash aid plugin and where do I get it from?

I have even difficulties to read this forum thread, it crashed 3 times until I managed to read the text.

The firefox is kind of needed here, but will try the chromium too.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

Flash-Aid is an extension that helps fix common flash issues, improve performance and allows to install the latest beta version. 

Besides Flash-Aid, install [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722/") and configure it to block flash or install [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433/"), so you can prevent unnecessary flash content from being loaded when you visit a page.

Also, start firefox in safe mode to see if the problem persists.

```
firefox -safe-mode
```

Check [http://www.webgapps.org/tutorials/firefox/troubleshooting/general-troubleshooting](http://www.webgapps.org/tutorials/firefox/troubleshooting/general-troubleshooting) for more troubleshooting methods and [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247") for know issues and solutions.

---

### Post by jramshu on 2011-07-23
+1 lovinglinux. 

I was on my Evo when I replied and it would have taken me forever to type as much as I would have liked to. 

I used to have a hard core attachment to FF when I used Windows. Since using Linux I lean more toward chromium, seems to run faster. Maybe it's just in my head and there isn't that much of a difference.

---

### Post by ottosykora on 2011-07-23
meanwhile tried to install seamonkey, chromium and latest flash from adobe website. Nothing seems to work on 11.04 while it all did perfect on 10,10 before :-(

I will try also the extension, but it looks like I have  no luck on 11.04, this version seems not to be compatible with any flash, regardless of what browser I use.

The actual intension was not to block flash, well then I could get rid of the plugin all together, but I wanted watch some videos delivered as flash.

---

### Post by lovinglinux on 2011-07-23
> **ottosykora said:**
> The actual intension was not to block flash, well then I could get rid of the plugin all together, but I wanted watch some videos delivered as flash.

Both extensions have a whitelist and placeholders, so if you want to watch a video on YouTube, you can whitelist YouTube or click the placeholder to watch a particular video. On other sites, where flash is used for fancy stuff and ads, you don't need to click them and they don't load automatically, thus saving a lot of CPU cycles.

---

### Post by ottosykora on 2011-07-23
well fine, but the flash seem not to work on 11.04 at all, what ever I install, it crashes as soon as it starts. So it looks like the upgrade to 11.04 was not best idea after all.

Tried so far firefox5, chromium and seamonkey, nothing works.

Firefox and Seamonkey do crash just by reading the forum here for example, chromium lets me read the forum, but the whole functionality is still very restricted so not much of use.

previous flash version: 10.3.181.34
after the flash aid: 11.0.1.60

but both behave same, therefore I assume that the whole thing is a problem on ubuntu 11.04 itself and not just on the browser side this time, thought the firfox5 does crash also on all sorts of scripts.

The graphic card should cope, it is rather new hp notebook 6550b with intel graphics.

All did work perfect on 10.10.

Also skype does  not work.

---

### Post by lovinglinux on 2011-07-23
> **ottosykora said:**
> well fine, but the flash seem not to work on 11.04 at all, what ever I install, it crashes as soon as it starts. So it looks like the upgrade to 11.04 was not best idea after all.

Tried so far firefox5, chromium and seamonkey, nothing works.

Firefox and Seamonkey do crash just by reading the forum here for example, chromium lets me read the forum, but the whole functionality is still very restricted so not much of use.

previous flash version: 10.3.181.34
after the flash aid: 11.0.1.60

but both behave same, therefore I assume that the whole thing is a problem on ubuntu 11.04 itself and not just on the browser side this time, thought the firfox5 does crash also on all sorts of scripts.

The graphic card should cope, it is rather new hp notebook 6550b with intel graphics.

All did work perfect on 10.10.

Also skype does  not work.

I suppose you upgraded from 10.10 to 11.04 instead of doing a clean install. Personally, I never do upgrades.

You could try to create a new Ubuntu user just to see if the problems persist. Sometimes is just your personal settings that came from 10.10 that are not playing well. Otherwise, I would recommend a clean install, since apparently you have multiple problems with multiple applications.

---

### Post by ottosykora on 2011-07-23
well clean install, could be a solution, but this takes mostly a week to do all the config and set up of all the additional software, nightmare!

What I did try was to run the 11.04 from the life CD and surprise: same effects there as on my installation. Browser crashing all the time, flash 'installed' onto the temporary environment under the life CD has same problems while it has no problems on other two installations of 10.10 on other , much slower and older computers.

Is there anything known about some flash incompatibility on 11.04?

---

### Post by ottosykora on 2011-07-23
OK, had to give on this for the time being.

Have restored the partition from backup to 10.10 , done all other updates on it and all works very fine, inclusive all browsers and the firefox too.

Will try in near future new install of 11.04, but it looks as this will not work as the life CD does not work too.
It might be the hardware, but it is rather standard recent version of HP notebook with standard intel chipset and graphic.

---

### Post by lovinglinux on 2011-07-23
> **ottosykora said:**
> well clean install, could be a solution, but this takes mostly a week to do all the config and set up of all the additional software, nightmare!

What I did try was to run the 11.04 from the life CD and surprise: same effects there as on my installation. Browser crashing all the time, flash 'installed' onto the temporary environment under the life CD has same problems while it has no problems on other two installations of 10.10 on other , much slower and older computers.

Is there anything known about some flash incompatibility on 11.04?

> **ottosykora said:**
> OK, had to give on this for the time being.

Have restored the partition from backup to 10.10 , done all other updates on it and all works very fine, inclusive all browsers and the firefox too.

Will try in near future new install of 11.04, but it looks as this will not work as the life CD does not work too.
It might be the hardware, but it is rather standard recent version of HP notebook with standard intel chipset and graphic.

I would advise to create a separate partition for home, so you can do clean installs without losing configurations and personal files.

---

### Post by ottosykora on 2011-07-24
I have separate home partition, so this is not the major problem.

But installing new version just and formating the old partition seems to me somehow strange recommendation, what are the updates supposed to be for then?

On the other hand, installation does change this and that also in the home folder, so it is full strange config things then later too.
Then since I have to change the grub2 to grub legacy on each real install, as I need the grub in the root partition, this alone is lot of extra work already. Then all the additional apps, all the configuration, well this would mean every few months a week work to set up reasonably useful system. If this is the general recommendation, I will try this, but then definitely such operating system is anything but realistic for any even slightly serious use. 

I tried to upgrade on my other systems, one is an old dell, one is an older dell desktop (abt 7 years old) , one is hp netbook abt 1 year old, one is toshiba notebook older type, none of them were able to do the upgrade to 11.04, only the hp netbook tried but all did crash on reboot and was not able to boot to linux any more.

Thisis why I tried on my latest computer, the HP pro book 6550b with intel chips in it.
But if this does not work, what then?

---

### Post by ottosykora on 2011-07-24
BTW:

somewhere I have read, that when I upgrade from 10.10 to 11.04, the whole system is upgraded to 64bit version if the hardware does support it, even if the original installation was 32 bit.

Can this be a problem? As the 64 bit versions are known to be much more less developed then 32bit, I would like to keep 32bit version after update to 11.04
Is there a way of doing it?

---

### Post by lovinglinux on 2011-07-24
> **ottosykora said:**
> I have separate home partition, so this is not the major problem.

But installing new version just and formating the old partition seems to me somehow strange recommendation, what are the updates supposed to be for then?

On the other hand, installation does change this and that also in the home folder, so it is full strange config things then later too.
Then since I have to change the grub2 to grub legacy on each real install, as I need the grub in the root partition, this alone is lot of extra work already. Then all the additional apps, all the configuration, well this would mean every few months a week work to set up reasonably useful system. If this is the general recommendation, I will try this, but then definitely such operating system is anything but realistic for any even slightly serious use. 

I tried to upgrade on my other systems, one is an old dell, one is an older dell desktop (abt 7 years old) , one is hp netbook abt 1 year old, one is toshiba notebook older type, none of them were able to do the upgrade to 11.04, only the hp netbook tried but all did crash on reboot and was not able to boot to linux any more.

Thisis why I tried on my latest computer, the HP pro book 6550b with intel chips in it.
But if this does not work, what then?

Is not a general recommendation, just personal preference. Since I have a separate home, I can do a clean install preserving all my general settings, themes, applications settings and personal files. I can also **[install all extra applications without hassle and in a batch with dpkg selections]("http://ubuntuforums.org/showpost.php?p=7157175&postcount=5")**, so for me it is a lot faster and less troublesome than doing an upgrade. I can get the new Ubuntu version, working exactly as before in less than 2 hours. 

With every new Ubuntu release some users experience serious trouble with upgrades. Nevertheless, there are users doing upgrades without problems for years, since the initial release of Ubuntu. I guess it depends on how deep you customize your system and hardware you have. 

BTW, Windows only offer the possibility of doing upgrades and they get messy as well. If you want to do a clean installation, you need to backup your personal files, drivers, all applications installers and settings, then install everything back, which is a major pita. Additionally, you need to spend hours turning off useless services that run by default and fixing the security issues, so how about that?

> **ottosykora said:**
> BTW:

somewhere I have read, that when I upgrade from 10.10 to 11.04, the whole system is upgraded to 64bit version if the hardware does support it, even if the original installation was 32 bit.

Can this be a problem? As the 64 bit versions are known to be much more less developed then 32bit, I would like to keep 32bit version after update to 11.04
Is there a way of doing it?

Never heard of that. The 32bit version is the recommended and the default selected in the Ubuntu download page. So, it wouldn't make sense to upgrade the packages to 64bit on a upgrade. Besides, such unilateral decision is not the kind of thing Ubuntu does.

---

