---
title: "Online Videos won't play -- Youtube just blank where video should be"
date: 2011-02-21
forum: General Help
---

### Post by nrundy on 2011-02-21
Anybody know how to fix this?

[http://img135.imageshack.us/i/blankyoutubevideos.png/](http://img135.imageshack.us/i/blankyoutubevideos.png/)

I have latest Adobe Flash installed. All firefox add-ons disabled. IcedTea is installed. Cookies are allowed. Popup blocker is off.

Ubuntu 10.04 LTS

---

### Post by Syed75 on 2011-02-21
Try reinstalling Flash.

---

### Post by sikander3786 on 2011-02-21
Try the flash-aid Firefox add-on to remove any conflicting flash packages and re-install the current one's.

[https://addons.mozilla.org/sl/firefox/addon/flash-aid/](https://addons.mozilla.org/sl/firefox/addon/flash-aid/)

---

### Post by nrundy on 2011-02-21
I reinstalled it. No luck.

Did a complete removal and then reinstalled. still no joy.

---

### Post by nrundy on 2011-02-21
> **sikander3786 said:**
> Try the flash-aid Firefox add-on to remove any conflicting flash packages and re-install the current one's.

[https://addons.mozilla.org/sl/firefox/addon/flash-aid/](https://addons.mozilla.org/sl/firefox/addon/flash-aid/)

will this still be applicable even when I've never installed anything but adobe-flashplugin?

---

### Post by philinux on 2011-02-21
For elimination purposes run FF in safe mode.

Close firefox.
Open a terminal.

```
firefox -safe-mode
```

---

### Post by Syed75 on 2011-02-21
sudo apt-get install faac faad lame non-free-codecs ubuntu-restricted-extras


[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by nrundy on 2011-02-21
I installed Flash-Aid and executed it and now YouTube is working

Thanks sikander.  From now on, will Flash-Aid manage Flash updates automatically? Or do I need to periodically "Execute" it to keep things working?

Do you know why this happened? I initally installed restricted extras and that's it. Flash worked initally. What happened?

---

### Post by Vaphell on 2011-02-21
no idea what happened, something got borked.
Flash aid not only helps installing flash, but also resolves possible conflicts and removes stuff - in short it does cleanup work so the flash plugin can exist in a tidy environment.

updates - it depends. I think that when you install 32bit version, addon installs repo version (32 bit is available) and leaves it to the package manager but if you have 64bit machine and install 64bit flash, the addon checks adobe website for newer versions and upgrades 'manually'. When there is newer flash 64bit you'll see a dialog that new version is detected, do you want to upgrade.

---

### Post by nrundy on 2011-02-21
I'm running 32 bit.

I noticed that the Ubuntu-updates that I get were showing Flash as being updated. I know when I updated Flash on MS Windows I always had to use the Adobe-flash uninstaller to avoid problems. Maybe the Ubuntu-updates aren't properly uninstalling the old flash before the new one is installed?

---

