---
title: "Need help with CompizConfig Settings Manager (CCSM) Problems"
date: 2009-08-05
forum: General Help
---

### Post by sushain97 on 2009-08-05
I have installed a ubuntu distribution onto a usb drive and updated it to the lastest version, it worked perfectly until I installed ccsm (CompizConfig Settings Manager), and used a few settings in it. Everything started going black so I rebooted the system and it loads perfectly until I go into my account, then it starts to make any window, or menu (Applications, places System) that i open turn black. For example if I click on the System Menu after I log in, it opens and goes black. Then, if I use Ctrl+Alt+F1 to kill compiz from the terminal, it does not help. Any help would be appreciated.

Thanks

---

### Post by ubudog on 2009-08-05
For now just uninstall it until we get it fixed.

---

### Post by sushain97 on 2009-08-05
If you want me to uninstall ccsm, how is that possible through the terminal, its the only way to do anything on the system now

---

### Post by synapsys on 2009-08-05
```
sudo apt-get remove ccsm
```

although that's only the settings manager.

---

### Post by sushain97 on 2009-08-05
I tried to remove ccsm and it said no such package existed, i then removed compiz but it did not help, any more help?

---

### Post by sushain97 on 2009-08-06
bump
has this happened to anyone before???

---

### Post by philinux on 2009-08-06
Should be this.

```
sudo apt-get remove compizconfig-settings-manager
```

you may have messed with a setting that the system cant handle, although removing this might not help.

---

### Post by sushain97 on 2009-08-06
I just did that but it seems not to have helped, is there a way to reset everything to the last update time (8.04 to 9.04)?

---

### Post by sushain97 on 2009-08-06
it works again, thanks guys

---

### Post by harry2006 on 2009-08-06
you're welcome

---

### Post by ubudog on 2009-08-06
Any time.  :)

---

### Post by AfterShockPivot on 2009-08-12
This might count as a bump, but I had the exact same problem when I enabled "blur" on CCSM, and now Ubuntu just starts getting black squares everywhere. I uninstalled "sudo apt-get remove compizconfig-settings-manager" with the fail proof console on log-in, but it still didn't change anything, HELP!!!

---

### Post by AfterShockPivot on 2009-08-12
Bump, I'm using Ubuntu 9.04

---

### Post by fatpandasays on 2009-10-05
I, too, have this same issue. Also resulted from selecting the blur option. removing/purging ccsm didnt seem to fix anything, any other ideas out there?

---

### Post by fatpandasays on 2009-10-05
ok, may have figured this out. once in X, i waited for everything to presumably finish loading, then Alt-F2'd. got blackness and some scrambled pixels on the panel, took it on faith that something would happen if i started typing, so i typed 'metacity --replace', hit enter. things stopped blacking out and i was able to go disable ccsm effects

---

