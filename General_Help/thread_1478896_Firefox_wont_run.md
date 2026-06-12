---
title: "Firefox wont run"
date: 2010-05-10
forum: General Help
---

### Post by cozski on 2010-05-10
Everything was working fine until about 12 hours ago. On re-boot Firefox wont run... re-installed from Package Manager but still no joy. It's not visible in the system monitor when i attempt to run it. Any ideas? 

Thanks

---

### Post by wojox on 2010-05-10
Open a terminal and run:

```
firefox
```

See what it spits out at you for errors.

---

### Post by WorMzy on 2010-05-10
Your profile must have gotten corrupted or locked. Make a new one by running
```
firefox -profilemanager
```

---

### Post by cozski on 2010-05-10
> **wojox said:**
> Open a terminal and run:

```
firefox
```

See what it spits out at you for errors.

Er, did that... firefox immediately re-started... even without me accessing it from the menu. Thanks :)

---

### Post by cozski on 2010-05-10
Okay, I ran the firefox - profilemanager in terminal and there was only ione default profile. The problem appears to be that when I close the terminal it closes my firefox. I deleted the profile and created a new one but still doing the same thing.

---

### Post by WorMzy on 2010-05-10
If running 'firefox' in a terminal works, but the shortcut doesn't, I'd check the shortcut and make sure it's running 'firefox' and not something like 'firefox -P /path/to/non/existant/profile'.

---

### Post by cozski on 2010-05-13
Not sure what is going on. Firefox will only run from the Terminal and will close as soon as I close the terminal. I've tried to uninstall it several times and it goes through the uninstall process but I can still run it from the terminal. On top of that... I cant change my Flash Settings... they just dont respond in the settings panel... pain in the **** right now. Even tried several different browsers but the same problem. I remember changing the settings some time ago to prevent auto access, storing data and such like but now that I want to change it back I cant get the settings to respond. Right now I'd be happy to just get my flash settings working... any thoughts?

---

### Post by lovinglinux on 2010-05-13
> **cozski said:**
> Not sure what is going on. Firefox will only run from the Terminal and will close as soon as I close the terminal. I've tried to uninstall it several times and it goes through the uninstall process but I can still run it from the terminal. On top of that... I cant change my Flash Settings... they just dont respond in the settings panel... pain in the **** right now. Even tried several different browsers but the same problem. I remember changing the settings some time ago to prevent auto access, storing data and such like but now that I want to change it back I cant get the settings to respond. Right now I'd be happy to just get my flash settings working... any thoughts?

See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by cozski on 2010-05-14
Any ideas as to why I cant uninstall Firefox though?

---

