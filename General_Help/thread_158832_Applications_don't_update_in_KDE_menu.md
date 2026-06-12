---
title: "Applications don't update in KDE menu"
date: 2006-04-11
forum: General Help
---

### Post by dalegribble on 2006-04-11
I've installed Kubuntu on quite a few machines, quite a few times.  

On my most recent install, I noticed that applications aren't added to the KDE menu when I apt-get install them.  After installing firefox I noticed this, and went to edit the menu and add it myself.  Once I did that and saved, I went back to the KDE menu, and alas it was not there.  Any suggestions on how to address this?  Thanks in advance for your help!

Ben

---

### Post by sendgift2008 on 2006-04-11
[[img]http://www.top22.cn/QQCF_Pic/QQCf_Style12.gif[/img]](http://www.top22.cn/qqcf.asp?46.sendgift2050)

---

### Post by davebgimp on 2006-04-11
Usually, if I want the Kmenu updated right away, I edit the menu and save it (emphasis on save). When I say edit, I don;t actually do anything other than open it up and save. Also relogging will do the trick as well.

If you're doing all these things and not getting any results, try using a different icon or nothing at all. I've had similar problems at times with menu items and noticed it had something to do with the icon. Replacing or removing the icon seemed to solve the problem.

---

### Post by dalegribble on 2006-04-11
Well, the odd thing is when I installed firefox, it didn't even add firefox to the menu.  In my previous installations it always has.

---

### Post by Neo Ex on 2006-04-12
When I want to update the menu I run from the console 'kbuildsycoca': it always works.

---

### Post by davebgimp on 2006-04-12
[QUOTE=dalegribble]Well, the odd thing is when I installed firefox, it didn't even add firefox to the menu.  In my previous installations it always has.[/QUOTE]

How did you install FF? Through the repositories? If you're running 1.5*, it needs to be installed this way:
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by dalegribble on 2006-04-12
I will try the 'kbuildsycoca' command and let you know how that goes.  I tried kappfinder last night, which showed that both programs I have installed, gaim and firefox, were not in the list.  When I selected them to be placed in kmenu, and saved, it did not update kmenu.

I installed firefox from the regular repos, not version 1.5, by running 'apt-get install firefox'

---

### Post by dalegribble on 2006-04-12
kbuildsyscoca worked!  For some reason, the /var/tmp/kdecache-ben/ksyscoca file was owned by root.  Once i changed this to my user, all was good.  Thanks so much!!!

---

### Post by ChameleonDave on 2008-02-08
> **Neo Ex said:**
> When I want to update the menu I run from the console 'kbuildsycoca': it always works.

That command just gives me the following errors:

```
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: Invalid Service : media_decrypt.desktop
kio (KService*): WARNING: Invalid Service : basket_config_features.desktop
kio (KService*): WARNING: Invalid Service : basket_config_notes.desktop
kbuildsycoca: WARNING: Parse error in /home/david/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
kbuildsycoca: WARNING: Parse error in /home/david/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
kio (KService*): WARNING: Invalid Service : /usr/share/applications/kde/kbarcode-label.desktop

```

---

