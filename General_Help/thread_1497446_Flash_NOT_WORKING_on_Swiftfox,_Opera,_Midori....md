---
title: "Flash NOT WORKING on Swiftfox, Opera, Midori..."
date: 2010-05-30
forum: General Help
---

### Post by vaiocomputer on 2010-05-30
But, oddly, is working in Chromium, Konqueror, and Arora.
I'm using 64 bit Ubuntu w/ the non-free flash from the Ubuntu repos.

In Swiftfox, flash appears as a blank white area (in youtube) that cannot be right-clicked.  When scrolling in Opera, flash has 'static.'

---

### Post by lovinglinux on 2010-05-30
Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by vaiocomputer on 2010-05-30
> **lovinglinux said:**
> Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).


How long will you maintain this add-on?  How long does it take before new flash updates are recognized by this add-on for the user to update?

---

### Post by lovinglinux on 2010-05-30
> **vaiocomputer said:**
> How long will you maintain this add-on?

I don't have any plans to stop providing updates for this add-on. 

> **vaiocomputer said:**
> How long will you maintain this add-on?  How long does it take before new flash updates are recognized by this add-on for the user to update?

New flash 64bit beta versions are not detected automatically. I must add them to the extension options. I will do this whenever I see new versions at Adobe. Once Mozilla approve this extension, which takes about three weeks, I will be able to provide new versions of the extension through Firefox add-ons manager. Nevertheless, every new version needs to be reviewed by Mozilla, which takes about a week.

There is no delay if you get the new versions through my web site instead of Firefox add-ons manager. Additionally, once the extension is approved, I will be able to provide a beta channel, that does not need to be reviewed by Mozilla, so new beta versions will be available through Firefox add-ons manager as soon as I upload them. You will need to install a beta version of my add-on to get these updates.

---

### Post by vaiocomputer on 2010-05-30
> **lovinglinux said:**
> I will do this whenever I see new versions at Adobe.

How often do you check?

---

### Post by lovinglinux on 2010-05-30
> **vaiocomputer said:**
> How often do you check?

Depends. Usually when I'm not busy writing other extensions :)

Adobe has released version 10.1rc6 already, but it is not working for me and I couldn't find a 64bit version of it, so I'm not including it yet.

Anyway, why do you need new versions so fast? Don't worry, I will be updating it regularly. I'm not going to stay a month without updating if a new version is available.

---

### Post by slooksterpsv on 2010-05-30
Install Chrome and install Flash, it works quite well. Are you using Ubuntu Software Center to install Flash or the .DEB from Adobe? I haven't tried swiftfox, but I will and let you know if it works for me. - 64-bit Ubuntu 10.04 Lucid Lynx here btw.

EDIT: Just installed it, it doesn't work on Swiftfox.
EDIT 2: Trying Opera, it's downloading... it works! Quite well too, don't know about static its dynamic and fluid. 

Do you have all the updates for the distro?

---

### Post by lovinglinux on 2010-05-30
It seems Swiftfox has some bug, because it is not recognizing the flash plugin, but it does recognize other plugins. Additionally, if I delete the pluginreg.dat file, which should force it to reload the list of installed plugins, then I doesn't recognize any plugins.

---

### Post by lovinglinux on 2010-05-30
There is definitely a bug in Swiftfox that prevents it from recognizing any new installed plugin. If you start Firefox using the same user profile, then close Firefox and start Swiftfox it does recognize the plugins, but they don't work. I would recommend switching to the default Firefox for now.

---

### Post by slooksterpsv on 2010-05-30
> **lovinglinux said:**
> There is definitely a bug in Swiftfox that prevents it from recognizing any new installed plugin. If you start Firefox using the same user profile, then close Firefox and start Swiftfox it does recognize the plugins, but they don't work. I would recommend switching to the default Firefox for now.

Firefox is bulky and slow, try Chrome. Does IceWeasel still work?

---

### Post by lovinglinux on 2010-05-30
> **slooksterpsv said:**
> Firefox is bulky and slow, try Chrome. Does IceWeasel still work?

Sorry, but I'm not looking for an alternative browser. Firefox works perfect for me and Chrome doesn't offer anything that could make me switch from Firefox. If you look my web site you will realize you are recommending Chrome to the wrong guy :)

Anyway, I was just reporting a possible bug that could be the cause of the OP problem.

---

